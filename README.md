# Proyecto de MLOps con Airflow, MLflow, MinIO y FastAPI

Este proyecto muestra la implementación de un entorno de MLOps utilizando Docker Compose. Incorpora herramientas como Airflow para la orquestación de tareas, MLflow para el seguimiento de experimentos y modelos, MinIO para el almacenamiento de objetos y FastAPI para servir modelos de ML. 

## Descripción General

El flujo de trabajo del proyecto es el siguiente:

1. **Airflow** se utiliza para orquestar las tareas de recolección de datos, transformación y entrenamiento de modelos.
2. **MLflow** registra los experimentos y almacena los modelos de machine learning.
3. **MinIO** proporciona un almacenamiento compatible con S3 para los artefactos generados durante los experimentos.
4. Aunque no se muestra en las imágenes, se ha planificado **FastAPI** para servir los modelos entrenados para inferencia.

## Estructura del Proyecto

El proyecto está organizado de la siguiente manera:

```plaintext
taller3-main/
│
├── app/                 # Código fuente de FastAPI para servir modelos
├── dags/                # DAGs de Airflow para la orquestación de tareas
├── data/                # Datos recolectados
├── logs/                # Logs generados por Airflow
├── minio/               # Datos de configuración de MinIO
├── docker-compose.yaml  # Definición de servicios con Docker Compose
├── Dockerfile           # Dockerfile para el servicio MLflow
└── README.md            # Este archivo
```

## Configuración e Instalación

Para ejecutar este proyecto, es necesario tener Docker y Docker Compose instalados en su máquina. Siga estos pasos para iniciar los servicios:

1. Clone el repositorio:
   ```
   git clone https://github.com/jtorresj96/taller3.git
   cd taller3-main
   ```

2. Construya y levante los servicios con Docker Compose:
   ```
   docker-compose up --build
   ```

3. Una vez que los servicios estén en funcionamiento, puede acceder a las interfaces web:
   - Airflow: `http://localhost:8080`
   - MinIO: `http://localhost:9000`
   - MLflow: `http://localhost:1880`
   - FastAPI (cuando esté implementado): `http://localhost:8000`

## Servicios

### Airflow

Airflow se utiliza para orquestar el flujo de trabajo completo del proyecto. El DAG `json_to_dataframe_and_train_model` realiza las siguientes tareas:

- **Carga y transformación de datos**: Recopila datos de una API y los transforma para el entrenamiento del modelo.
- **Entrenamiento de modelos**: Entrena un modelo de clasificación forestal y lo almacena en MinIO.
![imagen3](https://github.com/wpradab/proyecto2/assets/142359246/aa78923f-c847-4784-88c3-31294daf02d9)



### MLflow

MLflow rastrea los experimentos y almacena los modelos. Puede ver los detalles de las ejecuciones, incluidos los parámetros, las métricas y los artefactos asociados.

![imagen1](https://github.com/wpradab/proyecto2/assets/142359246/f2f15c8d-9f31-4a40-b864-20d743bfc88a)
![imagen](https://github.com/wpradab/proyecto2/assets/142359246/f0ec42d7-03af-4f21-8e64-678cf64f36a9)



### MinIO

MinIO proporciona almacenamiento de objetos para MLflow. Los modelos entrenados y otros artefactos se almacenan aquí.

![imagen2](https://github.com/wpradab/proyecto2/assets/142359246/b93a33a2-3042-469e-9123-2afa65135ef2)



### FastAPI

FastAPI se utilizará para servir los modelos entrenados.
## Integrantes

Juan David Torres Jimenez
William David Prada Buitrago
Ricardo Macias Bohorquez
