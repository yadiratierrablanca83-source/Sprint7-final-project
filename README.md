# Sprint7-final-project
Este proyecto realiza un análisis exploratorio de datos (EDA) y una segmentación avanzada de la base de usuarios de **ConnectaTel** para identificar patrones de consumo, limpiar anomalías en los registros y proponer recomendaciones comerciales estratégicas.

## 🎯 Objetivo del Proyecto
El objetivo principal es **evaluar el comportamiento histórico de uso (llamadas y mensajes) y las características demográficas de los clientes** para detectar ineficiencias en los datos actuales, perfilar segmentos clave y proponer mejoras en la oferta comercial de planes de telefonía.

## 📊 Datasets Utilizados
El análisis se basa en tres conjuntos de datos ubicados en la carpeta `/datasets/`:
*   `plans.csv`: Detalles y características de las tarifas oficiales de la compañía.
*   `users_latam.csv`: Datos demográficos de los usuarios (ID, nombre, edad, ciudad, fecha de registro y plan).
*   `usage.csv`: Registro histórico detallado de los consumos mensuales (tipo de servicio, duración y volumen).

## 🔄 Etapas del Análisis Realizadas
1.  **Carga e Inspección Inicial:** Importación de librerías (`pandas`, `seaborn`, `matplotlib`) y exploración de dimensiones (`.shape`) y tipos de datos (`.info()`).
2.  **Limpieza de Datos y Manejo de Ausentes:** Identificación de nulos lógicos (MAR) en consumos, tratamiento del ~92% de nulos en `churn_date` (usuarios activos) y corrección de valores *sentinels* (`-999` en edad, `?` en ciudades y fechas futuras).
3.  **Procesamiento y Agregación:** Creación de variables auxiliares para consolidar métricas históricas de llamadas y mensajes por cada usuario.
4.  **Análisis Exploratorio y Visualización (EDA):** Generación de histogramas por tipo de plan para evaluar sesgos en las distribuciones y detección de *outliers* mediante el método de Rango Intercuartílico (IQR).
5.  **Segmentación de Clientes:** Clasificación de usuarios mediante reglas lógicas en grupos por nivel de uso y rangos de edad.

## 🚀 Cómo Ejecutar el Notebook

Puedes ejecutar este análisis de forma local o directamente en la nube:

### Opción A: Google Colab (Recomendada)
1. Ve a [Google Colab](https://google.com).
2. Selecciona la pestaña **Subir** y carga el archivo `.ipynb` de este proyecto.
3. Asegúrate de subir la carpeta `/datasets/` al almacenamiento temporal de la sesión antes de correr las celdas.
4. Ejecuta el entorno de forma secuencial (`Entorno de ejecución > Ejecutar todas`).

### Opción B: Entorno Local (Jupyter Notebook)
Asegúrate de tener instalada la suite de Anaconda o las librerías necesarias mediante la terminal:
```bash
pip install pandas matplotlib seaborn numpy
```
Abre la terminal en la carpeta del proyecto y ejecuta:
```bash
jupyter notebook
```

## 🛠️ Guía de Reproducción rápida
Para replicar los resultados exactos del análisis ejecutivo, sigue este orden en las celdas del notebook:
1.  **Celda 1 (Carga):** Ejecuta la importación y lectura de los CSV para asegurar que las variables `plans`, `users` y `usage` estén listas.
2.  **Celda 2 (Limpieza):** Aplica las reglas de sustitución de la mediana para la edad y marcas de tiempo correctas.
3.  **Celda 3 (Agregación):** Ejecuta el bloque `.groupby()` para construir el DataFrame `user_profile`.
4.  **Celda 4 (Visualización):** Corre las funciones de `sns.histplot` y `sns.boxplot` para visualizar los insights en pantalla.
