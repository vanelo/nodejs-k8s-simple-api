# Notes
Video tutorial: https://www.youtube.com/watch?v=OgOqo0gOLlQ
## Creación del contenedor docker
- Para hacer buil del dockerfile
  `docker build -t node-hash .` (el punto indica de donde se quiere leer el archivo Dockerfile)

- Para listar imagenes
  `docker images`

- Para ejecutar node dentro del contenedor
  `docker run -p 3000:3000 node-hash`

- Para listar los contenedores en ejecucion
  `docker ps`

- Para parar la ejecucion de un contenedor
  `docker stop nombre-del-contenedor`

- Para eliminar el contenedor
 `docker rm nombre-del-contenedor`

## Creación de cluster de contenedor con Kubernetes
- Instalar kind `https://kind.sigs.k8s.io/docs/user/quick-start/` 
  - Mover la carpeta creada en `sudo mv ./kind /usr/local/bin/kind` para tenerlo disponible en la terminal
- Crear el cluster a partir del kubernetes/manifest.yaml
  `kind create cluster`
- Instalar kubectl `https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/`
- Listar nodos
  `kubectl get nodes`
- Para cargar la imagen que creamos dentro del contenedor/cluster
  `kind load docker-image node-hash`
- Para crear los nodos
  `kubectl apply -f kubernetes/manifest.yaml`
- Listar los deploys
  `kubectl get deploy`
- Listar los pods
  `kubectl get pods`
- Para ver los logs del nodo
  `kubectl logs deploy/hash-api`
- Proxy entre puertos
  `kubectl port-forward service/hash-api 3000:80`