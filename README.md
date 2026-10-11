# Ejercicio 8 - Modelo Entidad-Relación de un Sistema de Inventario y Órdenes de Compra

## Descripción
Este ejercicio consiste en diseñar un modelo Entidad-Relación (DER) para un sistema de gestión de inventario, depósitos, proveedores y órdenes de compra. El modelo permite administrar la distribución de productos en almacenes, la provisión por parte de proveedores y el proceso de compras corporativas.

## Entidades y atributos

### 1. Productos
Representa los artículos comercializados o almacenados.
- **id_productos**: identificador único del producto.
- **codigo de barra**: código de barras identificador.
- **descripcion**: detalle o descripción del producto.
- **peso**: peso del producto.
- **dimensiones**: medidas o tamaño del producto.
- **stock minimo de seguridad**: nivel mínimo de inventario permitido.

### 2. Deposito
Representa los almacenes o depósitos donde se resguardan los productos.
- **id_deposito**: identificador del depósito.
- **numero de deposito**: número asignado al depósito.
- **nombre**: nombre del depósito.
- **direccion**: ubicación física del depósito.
- **responsable a cargo**: persona encargada de la gestión del depósito.

### 3. Produc_dep
Entidad asociativa que controla la presencia y stock de productos en cada depósito.
- **id_productos**: identificador del producto.
- **id_deposito**: identificador del depósito.
- **stock disponible**: cantidad disponible del producto en ese depósito específico.

### 4. Proveedor
Representa a las empresas o agentes abastecedores de productos.
- **id_proveedor**: identificador del proveedor.
- **cuit**: número de identificación tributaria (CUIT).
- **codigo internacional**: código identificador internacional.
- **razon social**: nombre o razón social legal del proveedor.
- **pais origen**: país donde reside o proviene el proveedor.
- **persona contacto**: nombre del contacto directo.
- **correo electronico**: correo de contacto.

### 5. Proved_produc
Entidad asociativa que gestiona la provisión de productos por cada proveedor.
- **cuit o codigo internacional**: identificación del proveedor.
- **codigo barra**: código del producto provisto.
- **Stock disponible**: cantidad disponible provista.

### 6. Orden compra
Representa los pedidos formalizados de compra de productos.
- **id_orden**: identificador único de la orden.
- **numero orden**: número oficial de la orden de compra.
- **fecha emision**: fecha de generación de la orden.
- **estado**: estado actual de la orden (ej. pendiente, aprobada, entregada).
- **destino**: depósito o lugar de destino del pedido.

### 7. detalle_compra
Representa la especificación de ítems y precios contenidos dentro de una orden de compra.
- **numero orden**: número de la orden asociada.
- **codigo barra**: código del producto solicitado.
- **cantidad**: unidades solicitadas.
- **precio pactado**: precio acordado por unidad.

## Relaciones y cardinalidades
- **Productos – Proveedor (1:N)**: un proveedor suministra múltiples productos.
- **Productos – Produc_dep (1:1)** y **Deposito – Produc_dep (1:1)**: vincula productos con depósitos para llevar el control del stock localizado.
- **Proveedor – Proved_produc (1:N)** y **Productos – Proved_produc (1:N)**: gestiona la relación de abastecimiento entre proveedores e ítems de catálogo.
- **Orden compra – Deposito (1:N)**: un depósito puede recibir múltiples órdenes de compra destinadas a sus instalaciones.
- **Orden compra – detalle_compra (1:1)**: vincula la cabecera de la orden con sus detalles de ítems comprados.
- **Proveedor – detalle_compra (1:N)**: un proveedor puede figurar como emisor/proveedor en múltiples ítems de detalle de compras.

## Objetivo
Diseñar una base de datos que permita organizar de forma eficiente el control de stock en depósitos, monitorear la oferta y disponibilidad de productos por proveedor, y gestionar de extremo a extremo las órdenes de compra y sus detalles.

