# Diseño de un modelo de predicción para medir el impacto de una publicación en una red social basada en técnicas de Machine Learning
Este repositorio sirve para aquellos que quieran aprender a utilizar modelos de machine learning con procesamiento de texto e imagenes tomando como entradas a las publicaciones de la red social de Instagram con su propio contenido: likes, comentarios, titulo del post, categoria de la cuenta,seguidores, etc.
## Metodologia
Como se observa esta metodología esta compuesta por 5 etapas:
![METODOLOGIA](https://user-images.githubusercontent.com/60902706/74689257-79521700-51a8-11ea-80c3-7e1cf6a55d9d.PNG)
### 1) Extracción de datos
En esta etapa se aborda la recolección de la data (publicaciones situadas en la red social de Instagram, desde el año 2017 hasta el 2019). Se tomaron observaciones de 28 marcas de diferentes rubros de negocio. Se utilizo la libreía Instaloader para la extracción. Los datos extraidos fueron los siguientes: pie de la foto, metadatos, comentarios y la imagen.
### 2) Preprocesamiento de datos
En esta etapa se realiza un prepocesamiento a la base de datos para obtener las variables claves para la creación de los mejores modelos con machine learning. Se identificaron distintas variables, pero las que tomaron como base son las siguientes: número de likes, número de comentarios, título de la publicación y la imagen.
### 3) Transformación de datos
En esta etapa se aborda la creación de la variable Y y los 3 tipos de modelado: texto, extracción de caracteristicas de la imagen y CNN de la imagen.
#### -Creacion de variable Y
"1" se considera como popular y "0" como no popular.
Una publicación es considerada popular si esta contiene como mínimo 75 comentarios o 12774 likes.
![CREACION DE LA VARIABLE Y](https://user-images.githubusercontent.com/60902706/74692027-65f87900-51b3-11ea-9dfa-e64dd03d4af8.png)
#### -Procesamiento de texto
Este proceso toma como entradas el título de las publicaciones. Para la obtención de los vectores característicos se realiza serie de pasos de limpieza de datos y luego se utiliazn los metodos BoW, Tf-Idf y Word2Vec.
![TRANSFORMACION DE DATOS - NLP](https://user-images.githubusercontent.com/60902706/74692260-65acad80-51b4-11ea-85d0-a5257dcc7fb6.PNG)
#### -Procesamiento de Imagen
Este proceso toma como entradas las imagenes de las publicaciones. Para la extracción de características se realiza unas pequeñas modificaciones a la imagen como la redimensión del tamaño y el escalado a grises. Luego se le aplica los descriptores SURF, SIFT y ORB. Por último para obtener los valores de las entradas del modelo final, se utiliza K-means de diferentes tamaños (10, 50, 100, 200, 400).
![TRANSFORMACION DE DATOS - IMAGEN](https://user-images.githubusercontent.com/60902706/74692940-8b878180-51b7-11ea-8134-5a287f6a54c8.png)
### 4) Minería de datos
En esta etapa se corren distintos clasificadores de machine learning. La base de datos se divide en train(70%) y test(30%).
#### -Modelo con texto
- Se toman como entradas los valores creados con el método BoW, Tf-Idf y Word2Vec.
- Los clasificadores a utilizar son: Regresión Logística, SVM y Redes Neuronales.
#### -Modelado con Imagenes
- Se toman como entradas los valores creados con los descriptores SURF, SIFT y ORB aplicados con el metodo K-Means de 10, 50, 100, 200 y 400.
- Los clasificadores a utilizar son: Regresión Logística, SVM y Redes Neuronales.
#### Imagen con CNN
- Se toman como entradas las imagenes.
- Los pesos utilizados son de un modelo entrenado VGG16: "Imagenet".
- Se le agregan otras capas de neuronas para poder clasificar en 2 clases.
### 5) Interpretacion de los resultados
Para esta etapa se interpretan los resultados en base al modelo más adecuado. El resultado se da utilizando los parámetros de evaluacion:
- Confusión Matrix
- Accuracy
- Precisión
- Recall
- Curva de ROC
- AUC
