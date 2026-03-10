# Detección de fallos en sistemas industriales a partir de datos de vibración usando aprendizaje no supervisado y semi-supervisado  

## Trabajo Fin de Máster  

**Máster en Big Data y Ciencia de Datos**  
**Universidad Internacional de Valencia (VIU)**  
**Curso académico 2025–2026**  

**Alumno:** Xabier Amutxastegi Navarlaz 

**Director:** Dr. Josep Font Moré  

Repositorio del Trabajo Fin de Máster sobre detección temprana de defectos en rodamientos mediante análisis de señales de vibración y técnicas de aprendizaje automático.

## Dataset

El proyecto utiliza el Case Western Reserve University Bearing Dataset (CWRU):

https://engineering.case.edu/bearingdatacenter

Los datos corresponden a condiciones de operación a 1797 rpm con distintos tipos de defecto:

- Normal
- Inner Race (IR): 0,007", 0,014", 0,021"
- Ball (B): 0,007", 0,014", 0,021"

Los archivos .mat utilizados se encuentran en la carpeta:

data/

## Metodología

El desarrollo del proyecto sigue varias etapas orientadas al análisis y detección de fallos en rodamientos a partir de señales de vibración.

### 1. Preprocesamiento de datos

Las señales originales del dataset CWRU se someten a un proceso de limpieza y preparación que incluye:

- Carga y preparación de las señales de vibración
- Segmentación de las señales en ventanas temporales para su análisis

### 2. Análisis de la señal en el dominio del tiempo

En primer lugar se analizan las características de la señal en el dominio temporal:

- Identificación de unidades de medida y naturaleza de la señal
- Comparación de señales según el tipo de defecto
- Comparación según la severidad del daño

Además, se calculan diferentes **características temporales** que describen el comportamiento estadístico de la señal.

### 3. Análisis en el dominio de la frecuencia

Posteriormente se realiza el análisis espectral mediante la Transformada de Fourier (FFT), lo que permite estudiar:

- Distribución del contenido espectral
- Comparación de espectros según la severidad del daño
- Comparación entre distintos tipos de defecto

A partir del espectro se extraen **características espectrales** que sirven como variables de entrada para los modelos de aprendizaje automático.

### 4. Construcción del conjunto de características

Se genera un conjunto de características combinando:

- Características temporales
- Características espectrales

Posteriormente se aplican técnicas de **análisis de correlación y reducción de dimensionalidad** para mejorar la representación de los datos.

### 5. Modelos de aprendizaje automático

Se evalúan distintos enfoques para la detección de anomalías en rodamientos.

#### Enfoques semi-supervisados

- **Autoencoder convolucional 1D (1D-CAE)** entrenado únicamente con datos en estado saludable
- **One-Class Support Vector Machine (OC-SVM)** basado en características espectrales

#### Enfoques no supervisados

También se estudian técnicas de clustering para identificar patrones en los datos:

- **K-Means**
- **Gaussian Mixture Model (GMM)**
- **Clustering jerárquico aglomerativo (Ward)**

Estos métodos permiten identificar desviaciones respecto al comportamiento normal y diferenciar entre distintos tipos y niveles de severidad del daño.

## Estructura del repositorio

```
tfm-xamutxastegi-bearing-fault-detection
│
├── data/                # Archivos del dataset CWRU
├── figures/             # Figuras extraídas en el análisis
├── tfm-xamutxastegi-big-data-y-ciencia-de-datos-viu.ipynb
├── requirements.txt     # Dependencias del proyecto
└── README.md
```

## Instalación

Instalar las dependencias del proyecto:

pip install -r requirements.txt

