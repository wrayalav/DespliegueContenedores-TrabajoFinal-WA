# Curso: Despliegue de aplicaciones con Docker<br/>CEC-EPN<br/><br/>Trabajo Final:  Despliegue de entornos de automatización con n8n integrados con PostgreSQL en Docker Compose

![Servidor de contenedores][cont-shield]
![Orquestacion de contenedores][ccom-shield]
![Automatizacion][n8n-shield]
![Base de datos][bdd-shield]

## Integrantes Grupo 3

- [Glenda Pallo](https://github.com/glendypallo/DespliegueContenedores-TrabajoFinal-GP)
- [Patricia Jaramillo](https://github.com/PatyJaramillo/DespliegueContenedores-TrabajoFinal-PJ)
- [William Ayala](https://github.com/wrayalav/DespliegueContenedores-TrabajoFinal-WA)
- [Guillermo Cifuentes](https://github.com/guillogps/DespliegueContenedores-TrabajoFinal-GC)
- [Ruperto Cisneros](https://github.com/srcisnerosv-star/DespliegueContenedores-TrabajoFinal-RC)

<br/>

## Introducción

El despliegue de entornos de automatización basados en contenedores constituye una práctica esencial en el desarrollo de soluciones modernas y escalables. En este trabajo se implementa la orquestación de n8n junto con una base de datos PostgreSQL mediante Docker Compose, aplicando principios de separación de servicios, persistencia de datos y seguridad en el manejo de credenciales.

La configuración definida contempla el uso de volúmenes para garantizar la persistencia de la información, una red dedicada para la comunicación interna entre servicios y un archivo .env que centraliza los parámetros sensibles como usuarios, contraseñas y claves de cifrado. Adicionalmente, se incorpora un healthcheck sobre la base de datos, lo que asegura que n8n únicamente inicie cuando PostgreSQL se encuentre disponible, reforzando la estabilidad del sistema.

<br/>

## Construido con

- Docker
- Docker Compose
- [PostgreSQL](https://hub.docker.com/_/postgres)
- [n8n](https://hub.docker.com/r/n8nio/n8n)

<br/>

## Archivos

La tarea contiene los siguientes archivos:

```
.
├── demostracion.json
├── docker-compose.yml
└── .env
```

| Archivo | Descripción |
| ---- | ---- |
| [.env](.env) | Variables de entorno necesarias para inicializar y administrar la base de datos consultorio. |
| [docker-compose.yml](docker-compose.yml) | Archivo que define la orquestación. |
| [demostracion.json](demostracion.json) | Ejemplo de automatización con n8n. |

<br/>

## Procedimiento

### Despligue

1. Comprobar que no se encuentren descargadas otras imágenes, creados otras redes que no sean por defecto, y que no existan contenedores en ejecución

   ```
   $ docker images
   $ docker network ls
   $ docker ps -a
   ```

   <img width="2048" height="1073" alt="image" src="https://github.com/user-attachments/assets/46791195-3b64-4c92-a2b3-967428ef4346" />

2. Se despliegan los contenedores del trabajo final

   ```
   $ docker compose up -d
   ```

   <img width="2048" height="1070" alt="image" src="https://github.com/user-attachments/assets/368e42c0-f67a-4b3f-b5df-e32ab1c5e492" />

   <img width="2048" height="1062" alt="image" src="https://github.com/user-attachments/assets/18df45e9-e015-48d3-9cb3-1f931ff6de59" />

3. Se comprueba la descarga de las imágenes, la creación de la red, y el despliegue de los dos contenedores (PostgreSQL y n8n)

   <img width="2048" height="1068" alt="image" src="https://github.com/user-attachments/assets/6d30ef99-2770-492e-9f18-ba528b5fe422" />

4. Se revisa los logs para identificar cualquier problema durante el despliegue

   <img width="2048" height="1068" alt="image" src="https://github.com/user-attachments/assets/8d9e80d5-3c1f-45a8-b508-778f94bb6f90" />

   <img width="2048" height="1065" alt="image" src="https://github.com/user-attachments/assets/452a644d-704a-466c-8b7f-67800778c8c8" />

5. Se abre un explorador web para acceder al portal del n8n

   <img width="2048" height="1071" alt="image" src="https://github.com/user-attachments/assets/a6c61900-9b78-4603-af92-7a5a63db5108" />

### Prueba de utilización del n8n

1. Creación de un usuario

   <img width="2048" height="1066" alt="image" src="https://github.com/user-attachments/assets/89557f2c-4f01-4c25-b17d-6e58ada7aa90" />

2. Se ignora los dos mensajes iniciales para acceder a la versión gratis para pruebas (Community)

   <img width="2048" height="1069" alt="image" src="https://github.com/user-attachments/assets/305c5ced-07bd-4c51-94f8-1787637b4313" />

   En esta ventana emergente no se debe seleccionar ninguna opción y solo se debe presionar el botón `Get Started`

   <img width="2048" height="1065" alt="image" src="https://github.com/user-attachments/assets/ea0d0350-ed6e-49e8-8e8c-ae8078ebc0bc" />

   En esta ventana emergente se debe presionar el botón `Skip`

3. Se visualiza la página inicial del n8n

   <img width="2048" height="1069" alt="image" src="https://github.com/user-attachments/assets/1fc76204-2423-425f-a187-54b4e278895c" />

4. Al presionar el el botón `Start from scratch` se despliega lo siguiente

   <img width="2048" height="1152" alt="image" src="https://github.com/user-attachments/assets/ce84e35c-0898-42ba-88aa-e18a209faa47" />

5. Ahora cargamos un ejemplo previamente elaborado ([demostracion.json](demostracion.json)), para lo cual se presionan los tres puntos de la parte superior de la página

   <img width="2048" height="1066" alt="image" src="https://github.com/user-attachments/assets/4b8c2844-11f7-445b-a060-be3a10940f38" />

   <img width="2048" height="1067" alt="image" src="https://github.com/user-attachments/assets/5d994461-0ae0-4288-8f8f-a901ab88f5e9" />

6. Antes de realizar la prueba del Workflow, es necesario hacer clic sobre el elemento `Webhook` para obtener la dirección web de pruebas del api a consumir

   <img width="2048" height="1066" alt="image" src="https://github.com/user-attachments/assets/7ca7efdf-12c6-47ed-b2ff-70f9033663f4" />

   ```
   http://localhost:5678/webhook-test/test
   ```

7. Presionamos el botón `Exceute workflow` para que el flujo entre en un estado de espera

   <img width="2048" height="1068" alt="image" src="https://github.com/user-attachments/assets/6e92c103-5f07-466e-9606-8abfc273b736" />

8. Desde el terminal ejecutamos el comando curl

   ```
   $ curl http://localhost:5678/webhook-test/test
   ```

   <img width="2048" height="1067" alt="image" src="https://github.com/user-attachments/assets/4effb42d-4fa7-4105-a5ac-adf5302864c2" />

   Y comprobamos el mensaje de salida

9. Regresamos al n8n para observar el estado del workflow

   <img width="2048" height="1070" alt="image" src="https://github.com/user-attachments/assets/950bf43d-af8a-42f1-bec2-ad8ff776f0ec" />

   Como se puede observar el workflow se ejecutó según lo configurado

<br/>

## Conclusiones

- La implementación de n8n con PostgreSQL en Docker Compose demuestra la viabilidad de construir entornos de automatización robustos y seguros empleando contenedores.
- El uso de volúmenes asegura la persistencia de la información, mientras que la definición de credenciales en un archivo .env facilita la portabilidad del proyecto y evita la exposición de datos sensibles en el código.
- Asimismo, la inclusión de parámetros de seguridad como: N8N_ENCRYPTION_KEY que define la semilla de encriptación de las claves de usuario, N8N_BLOCK_ENV_ACCESS_IN_NODE que restringe el acceso a las variables de entorno desde los nodos del workflow, y la autenticación en la interfaz web fortalecen la protección del sistema.
- La configuración presentada cumple con los criterios de buenas prácticas solicitados en el proyecto: aislamiento de servicios, modularidad y reproducibilidad.

<!-- MARKDOWN LINKS & IMAGES -->
[cont-shield]: https://img.shields.io/badge/CONTAINER-DOCKER-red?style=for-the-badge&logo=docker
[ccom-shield]: https://img.shields.io/badge/CONTAINER-DOCKER%20COMPOSE-blue?style=for-the-badge&logo=docker
[n8n-shield]: https://img.shields.io/badge/WORKFLOW-N8N-green?style=for-the-badge&logo=n8n
[bdd-shield]: https://img.shields.io/badge/BDD-POSTGRESQL-magenta?style=for-the-badge&logo=postgresql
