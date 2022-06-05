# Trabajo3Telematica


## Punto 1, Cargar Datos
Para la cargo de datos como requisito previo debemos descargar el archivo csv (https://www.datos.gov.co/api/views/gt2j-8ykr/rows.csv?accessType=DOWNLOAD). Una vez descargado, en nuestro Google Drive creamos una carpeta llamada "st0263trabajo3" (IMPORTANTE, esta carpeta debe estar ubicada en la raiz de tu drive, es decir, no estar dentro de otra carpeta) y dentro de esta carpeta cargamos el archivo csv. 

![image](https://user-images.githubusercontent.com/71454879/172069568-dc70e657-f45f-4512-9e39-70790024048d.png)
La celda 7 del cuaderno ipynb es la encargada de cargar los datos una vez ubicados en la ubicación correcta. 


## Punto 2, análisis exploratorio del Dataframe
Dentro del Dataframe podemos hacer diferentes operaciones, a continuación se ejemplifican algunas de ellas:

### Columnas:
![image](https://user-images.githubusercontent.com/71454879/172069811-61571026-501a-48a0-b18b-76e94c98757e.png)

### Tipos de datos:
![image](https://user-images.githubusercontent.com/71454879/172069778-0bf995a6-559c-4ce9-b309-8988fed6b28f.png)

### Seleccionar algunas columnas:
![image](https://user-images.githubusercontent.com/71454879/172069858-481c58c7-2e5e-481d-be3b-d1dfdd16afbc.png)

### Renombrar columnas:
![image](https://user-images.githubusercontent.com/71454879/172069940-92f7a2c0-9032-4932-bba9-f927c8df1a8c.png)

### Agregar columnas:
![image](https://user-images.githubusercontent.com/71454879/172070055-a6878257-e772-4b7c-a0f5-f4be36f19a4b.png)

### Borrar columnas:
![image](https://user-images.githubusercontent.com/71454879/172070122-f9500289-97cd-4ff7-9770-a6df14e9b51d.png)

### Filtrar datos:
![image](https://user-images.githubusercontent.com/71454879/172070201-91e4f05f-e4ee-4a38-b758-b5b150056706.png)

### Usar funciones UDF:
![image](https://user-images.githubusercontent.com/71454879/172070554-98d9f2e5-a0d0-471b-9292-2fb7858cdfb9.png)


## Punto 3
Estas consultas al dataframe siguen una lógica muy similar, funcionando bajo las funciones groupBy(), count() y orderBy() de pyspark. La primera nos agrupa los datos en función de la columna que tenga como parametro, la segunda cuenta los registros que hay por cada agrupación que se hizo previamente (datos distintos) y la tercera nos define la forma de ordenarlos.

### 3.1 
![image](https://user-images.githubusercontent.com/71454879/172070766-bc03e623-d53b-420b-b91e-ca924a72be6b.png)

### 3.2
![image](https://user-images.githubusercontent.com/71454879/172070797-9f4a96c6-4214-4e5c-9298-eb668a13cea2.png)

### 3.3
![image](https://user-images.githubusercontent.com/71454879/172070902-1deebc4f-979a-4136-acab-3965d04397ee.png)

### 3.4
![image](https://user-images.githubusercontent.com/71454879/172071117-39692909-40ef-4edb-984a-d7dbbc056e5d.png)

### 3.5
En este caso previamente se debe hacer una transformación al dataframe para convertir el tipo de dato de la columna "Fecha de diagnóstico" de String a Date, esto con miras a usar la propia función month() de pyspark para obtener el mes de la fecha.
![image](https://user-images.githubusercontent.com/71454879/172071480-1bd41c83-94cd-4796-bb64-4dc26f3a61e5.png)

### 3.6 ¿Cual es el porcentaje de defunción?
![image](https://user-images.githubusercontent.com/71454879/172071714-d3f04ac0-5d73-4f3f-96db-2da4cc8917f2.png)

## Exportar datos de salida
Para la exportación de los datos de salida, el primer paso será eliminar la función show() de todas nuestras consultas, esto debido a que show() hace que lo que nos retorne la consulta, ya no sea un dataframe sino simplemente una vista. Después de esto se creará una carpeta en el Google Drive llamada "outputs"; en esta carpeta irán todos los outputs. 
![image](https://user-images.githubusercontent.com/71454879/172073135-a3319fe5-f64b-4bf8-b928-028d7f6a5487.png)

Asignaremos a una variable el dataframe nuevo que se obtiene con la consulta, en este caso esa variable es "data", luego se define la uri de la ubicación a donde queremos enviar el csv, en este caso además se ha definido que cada consula irá en una subcarpeta diferente (ver final de la uri en que dice la carpeta "3.4" para ese caso en particular). Finalmente se exporta el dataframe contenido en "data" en formato csv hacia la uri especificada. 

Todos los numerales del punto 3 han sido exportados a excepción del numeral 3.6 pues no lo que retorna es un unico valor.
