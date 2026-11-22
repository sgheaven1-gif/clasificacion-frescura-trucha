CLASIFICACION DEL ESTADO DE FRESCURA DE LA TRUCHA ARCOIRIS A PARTIR DE LA REGION OCULAR

Codigo de la tesis de pregrado "Optimización del método Quality Index mediante el uso de inteligencia artificial para la determinación del grado de frescura de truchas en la región de Puno" (Escuela Profesional de Ingeniería Electrónica, Universidad Nacional del Altiplano – Puno).

Se comparan seis arquitecturas preentrenadas en ImageNet (DenseNet121, EfficientNet-B0, InceptionV3, MobileNetV2, ResNet50 y ResNeXt50 32x4d) para clasificar el día de conservación (1, 3, 5, 7 y 9) a partir de imágenes del ojo, en tres escenarios:

  - Escenario 1 (E1): 5 clases (días 1, 3, 5, 7 y 9)
  - Escenario 2 (E2): 2 clases (días 1 y 9)
  - Escenario 3 (E3): 3 clases (días 1, 5 y 9)

Cada combinación de arquitectura, escenario y configuración (P1, P2, P3) se entrenó con tres semillas (42, 123, 2026) con el optimizador Adam: 162 corridas. Además se entrenaron 9 corridas de una línea base con SGD (ResNeXt50 32x4d).


CONTENIDO

  pipeline_clasificacion_frescura_trucha.ipynb
      Cuaderno con el pipeline completo (Google Colab o servidor): verificación de datos, entrenamiento, selección del mejor punto de control por validación, evaluación en prueba y tablas/figuras.


DATOS

El conjunto de datos está formado por recortes de la región ocular de truchas arcoíris conservadas en hielo (días 1, 3, 5, 7 y 9), elaborados a partir de fotografías de Mamani Flores y Pedraza Huisa (2023). Las imágenes NO se incluyen en este repositorio. Estructura esperada:

  tesis_2026:
  escenario1/pruebas_2026_1/truchas_ojos/{train,value,test}/{1,3,5,7,9}/
  escenario2/pruebas_2026_2/truchas_ojos/{train,value,test}/{1,9}/
  escenario3/pruebas_2026_3/truchas_ojos/{train,value,test}/{1,5,9}/

Las rutas se configuran en la primera celda del cuaderno (diccionario RUTAS).


ENTORNO

Python 3.10, PyTorch 2.14.1, torchvision 0.29.2, pandas 2.3.3, matplotlib 3.10.9, seaborn 0.13.2, scikit-learn 1.7.2. Entrenado en 2 GPU NVIDIA RTX A6000.


USO

Entrenamiento y evaluación: abrir el cuaderno, elegir ENTORNO = "colab" o "servidor" en la primera celda, ajustar las rutas y ejecutar las celdas en orden. Las corridas ya terminadas se omiten si se vuelve a ejecutar.

Para conservar los pesos de cada corrida, poner GUARDAR_PESOS = True en la primera celda; se guardan como archivos .pt en la carpeta modelos/.


ALCANCE Y LIMITACIONES

El sistema ayuda a optimizar el Quality Index Method (QIM) al automatizar uno de sus atributos visuales, la apariencia ocular, sin sustituir la evaluación sensorial integral. Se utiliza un único atributo visual, la región ocular, y los mejores resultados se obtienen al distinguir estados contrastantes de frescura (2 y 3 clases).


REFERENCIA

Mamani Flores, E. W., & Pedraza Huisa, R. (2023). Clasificación de la frescura del pescado utilizando una red neuronal convolucional [Tesis de pregrado, Universidad Peruana Unión]. https://hdl.handle.net/20.500.12840/7367
