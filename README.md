# TechRetail - Docker Swarm Deployment

## Créditos

* Santos Zuasnabar, Paulo Nicolas - FullStack junior

## 📌 Descripción

Este proyecto implementa un clúster Docker Swarm para la empresa TechRetail, con el objetivo de mejorar la escalabilidad y disponibilidad del sistema.

## 🏗️ Arquitectura

* 1 nodo Manager
* 2 nodos Worker

```
┌───────────────────────────────────────────────┐
│           Docker Swarm Cluster                │
│                                               │
│   ┌───────────────────────────────┐           │
│   │           MANAGER             │           │
│   │  Role: Leader                │           │
│   │                               │           │
│   │  - database (MySQL)           │           │
│   │  - visualizer                 │           │
│   │  - frontend (réplicas)        │           │
│   │  - backend (réplicas)         │           │
│   └───────────────────────────────┘           │
│                                               │
│   ┌───────────────────────┐   ┌───────────────────────┐
│   │       WORKER 1        │   │       WORKER 2        │
│   │                       │   │                       │
│   │  - frontend (x2)      │   │  - frontend (x2)      │
│   │  - backend (x1)       │   │  - cache (Redis)      │
│   │                       │   │                       │
│   └───────────────────────┘   └───────────────────────┘
│                                               │
│   🔄 Comunicación: Red Overlay (techretail_net)│
│   ⚖️ Balanceo: Docker Swarm Load Balancer      │
└───────────────────────────────────────────────┘
```


## ⚙️ Servicios

* Frontend (Nginx)
* Backend (Node.js)
* Base de datos (MySQL)
* Cache (Redis)
* Visualizer

## 🚀 Despliegue

```bash
docker swarm init
docker stack deploy -c docker-compose.yml techretail
```

## 📈 Escalabilidad

```bash
docker service scale techretail_frontend=5
```

## 🌐 Acceso

* Frontend: http://98.82.25.229
* Visualizer: http://98.82.25.229:8080

## 📄 Informe y Evidencias

Ver carpeta /docs