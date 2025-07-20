# Optimización de Redes de Transporte Urbano con Deep Learning

Este proyecto forma parte del Trabajo de Fin de Estudios (TFE) y tiene como objetivo aplicar técnicas de aprendizaje profundo para predecir la intensidad de tráfico en redes urbanas, utilizando datos reales de la ciudad de Madrid.

## 🚦 Motivación

Madrid ha experimentado un incremento progresivo del tráfico vehicular en los últimos años. Esta situación exige soluciones inteligentes que permitan anticipar la congestión y optimizar la movilidad. La inteligencia artificial, y en particular el Deep Learning, representa una herramienta potente para afrontar este reto.

## 🧠 Modelos utilizados

Se compararon distintos algoritmos de Machine Learning y Deep Learning:

- **XGBoost**
- **K-Nearest Neighbors (KNN)**
- **Convolutional Neural Networks (CNN)**
- **Long Short-Term Memory (LSTM)**
- **Gated Recurrent Unit (GRU)**
- **LSTM + GRU (modelo híbrido)**

## 📊 Datos

- **Fuente:** Estaciones de monitoreo de tráfico de la M-30 (Ayuntamiento de Madrid)
- **Periodo:** Enero 2023 – Marzo 2024
- **Variables utilizadas:**
  - Intensidad, velocidad media, ocupación, carga
  - Día de la semana, hora del día, temperatura
  - Si es festivo o no

## 🧹 Preprocesamiento

- Limpieza de datos
- Manejo de valores nulos (media por campo)
- Reformateo de fechas
- Eliminación de columnas irrelevantes
- Selección de características clave

## 📈 Entrenamiento y evaluación

Los notebooks están organizados para seguir una secuencia de análisis y modelado. Se incluyen secciones de:

- Análisis exploratorio de datos
- Transformación y preparación de datos
- Entrenamiento de modelos
- Evaluación de métricas (MAE, MSE, RMSE, R²)

## 🥇 Principales resultados

### Todas las estaciones
El modelo **GRU** obtuvo los mejores resultados, este tiene un buen balance entre precisión y rapidez en la predicción con datos no vistos.

| | Modelo        | Tiempo entrenamiento | Tiempo predicción | R^2 | 
|--|---------------|----------------------|--------------------|-----|
|5 | XGBoost       | 1m 15s               | 2s                | 0.99369 |
|6 | KNN           | 1s                   | 0.1s              | 0.99279 |
|7 | CNN           | 1m 36s               | 1s                | 0.98855 |
|3 | LSTM          | 10m 34s               | 3s                | 0.99446 |
|1 | **GRU**           | **13m 3s**              | **2s**               | **0.99590** |
|2 | LSTM + GRU    | 10m 15s              | 2s                | 0.99517 |
|4 | LSTM + GRU (4 capas) | 43m 30s       | 7s               | 0.99407 |

### Estación 6667
El modelo **XGBoost** obtuvo los mejores resultados y requiere reducido tiempo de entrenamiento.

| Posicion | Modelo        | Tiempo entrenamiento | Tiempo predicción | R^2 | 
|--|---------------|----------------------|--------------------|-----|
|1 | **XGBoost**       | **1m 6s**                | **2s**                | **0.96055** |
|2| KNN           | 1s                   | 0.1s              | 0.95891 |
|7 | CNN           | 1m 34s               | 1s                | 0.85709 |
|5 | LSTM          | 10m 6s               | 3s                | 0.94333 |
|4 | GRU           | 9m 48s              | 2s               | 0.94595 |
|3 | LSTM + GRU    | 13m 14s              | 2s                | 0.95090 |
|6 | LSTM + GRU (4 capas) | 43m 26s       | 11s               | 0.93283 |

## 🛠 Instrucciones para correr los notebooks

1. Clona el repositorio:
git clone https://github.com/wilsongitdev/TFE_Transporte.git
cd TFE_Transporte

2. Crea y activa un entorno virtual (opcional):
python -m venv venv
source venv/bin/activate  # En Windows: venv\Scripts\activate

3. Instala los requerimientos:
Este proyecto requiere Python 3.8+ y las siguientes librerías
- numpy
- scikit-learn
- xgboost
- tensorflow
- keras
- pandas
- matplotlib
- seaborn

4. Abre los notebooks en Jupyter o VSCode

## 📂 Estructura del proyecto

```
TFE_Transporte/
├── data/ # Datos crudos y preprocesados
├── notebooks/ # Notebooks Jupyter (.ipynb)
│ ├── EDA.ipynb # Análisis exploratorio de datos
│ ├── Estacion_6667.ipynb # Modelos con datos de la estación 6667
│ └── Todas_Estaciones.ipynb# Modelos con todas las estaciones
├── requirements.txt # Librerías necesarias
└── README.md # Este archivo
```
## 🚀 Líneas futuras
- Analizar en qué situaciones se generan los mayores errores de predicción
- Optimizar los modelos para predicciones más largas (30-60 minutos)
- Subir el modelo a la nube para su explotación práctica
- Explorar nuevas arquitecturas híbridas que incluyan XGBoost
## 👨‍💻 Autores
- Wilson Manuel Chavesta Gonzales
- Miguel Ángel Sánchez Pérez
- Bryan Andrey Fierro Ocampo
Director: Jesús Cigales Canga
📅 Abril 2025

## 📚 Referencias
Aquí se listan algunas de las más relevantes:

- Chen, C., Liu, Z., Wan, S., Luan, J., & Pei, Q. (2021). Traffic Flow Prediction Based on Deep Learning in Internet of Vehicles. IEEE Transactions on Intelligent Transportation Systems, 22(6), 3776–3789. https://doi.org/10.1109/TITS.2020.3025856

- Zafar, N., Haq, I. U., Chughtai, J. U. R., & Shafiq, O. (2022). Applying Hybrid Lstm-Gru Model Based on Heterogeneous Data Sources for Traffic Speed Prediction in Urban Areas. Sensors, 22(9). https://doi.org/10.3390/s22093348

- Ayuntamiento de Madrid. (n.d.-a). Censo de Población y Viviendas 2021 - Ayuntamiento de Madrid. Retrieved November 30, 2024, from https://www.madrid.es/portales/munimadrid/es/Inicio/El-Ayuntamiento/Estadistica/Areas-de-informacion-estadistica/Demografia-y-poblacion/Censos-de-Poblacion/Censo-de-Poblacion-y-Viviendas-2021/?vgnextfmt=default&vgnextoid=772b6f7c0af08810VgnVCM1000001d4a900aRCRD&vgnextchannel=583011fc98916410VgnVCM2000000c205a0aRCRD


📬 Para dudas o sugerencias: wilsonmanuel.chavesta655@comunidadunir.net
