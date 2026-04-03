# CST8915 Lab 8 - Full-stack Cloud-native Development: Deploying and Managing the Algonquin Pet Store (On Steroids)

**Student Name**: IDRIS JOVIAL SOP NWABO

**Student ID**: 041199877

**Course**: CST8915 Full Stack Cloud Native Development

**Semester**: Winter 2026


---

## Demo Video

🎥 [Watch Demo Video](https://www.youtube.com/watch?v=PhPo4Z-0FAg)

---

## Architecture

The application has the following services: 

| Service | Description | Github Repo | Docker Image |
| --- | --- | --- | --- |
| `store-front` | Web app for customers to place orders (Vue.js) | [store-front-L8](https://github.com/ramymohamed10/store-front-L8) | [ramymohamed/store-front-l8](https://hub.docker.com/r/ramymohamed/store-front-l8) |
| `store-admin` | Web app used by store employees to view orders in queue and manage products (Vue.js) | [store-admin-L8](https://github.com/ramymohamed10/store-admin-L8) | [ramymohamed/store-admin-l8](https://hub.docker.com/r/ramymohamed/store-admin-l8) |
| `order-service` | This service is used for placing orders (Javascript) | [order-service-L8](https://github.com/ramymohamed10/order-service-L8) | [ramymohamed/order-service-l8](https://hub.docker.com/r/ramymohamed/order-service-l8) |
| `product-service` | This service is used to perform CRUD operations on products (Rust) | [product-service-L8](https://github.com/ramymohamed10/product-service-L8) | [ramymohamed/product-service-l8](https://hub.docker.com/r/ramymohamed/product-service-l8) |
| `makeline-service` | This service handles processing orders from the queue and completing them (Golang) | [makeline-service-L8](https://github.com/ramymohamed10/makeline-service-L8) | [ramymohamed/makeline-service-l8](https://hub.docker.com/r/ramymohamed/makeline-service-l8) |
| `ai-service` | Optional service for adding generative text and graphics creation (Python) | [ai-service-L8](https://github.com/ramymohamed10/ai-service-L8) | [ramymohamed/ai-service-l8](https://hub.docker.com/r/ramymohamed/ai-service-l8) |
| `rabbitmq` | RabbitMQ for an order queue | [rabbitmq](https://github.com/docker-library/rabbitmq) | [rabbitmq:3-management](https://hub.docker.com/_/rabbitmq) |
| `mongodb` | MongoDB instance for persisted data | [mongodb](https://github.com/docker-library/mongo) | [mongo:4.2](https://hub.docker.com/_/mongo) |
| `virtual-customer` | Simulates order creation on a scheduled basis (Rust) | [virtual-customer-L8](https://github.com/ramymohamed10/virtual-customer-L8) | [ramymohamed/virtual-customer-l8](https://hub.docker.com/r/ramymohamed/virtual-customer-l8) |
| `virtual-worker` | Simulates order completion on a scheduled basis (Rust) | [virtual-worker-L8](https://github.com/ramymohamed10/virtual-worker-L8) | [ramymohamed/virtual-worker-l8](https://hub.docker.com/r/ramymohamed/virtual-worker-l8) |


![Logical Application Architecture Diagram](assets/Algonquin%20Pet%20Store%20On%20Steroids.png)

## Run the app on Azure Kubernetes Service (AKS)

You can use the kubernetes YAML files provided in the [Deployment Files](./Deployment%20Files/) folder to deploy the app to an AKS cluster.

 - Login to your azure account using the following command:
	```
	az login
	```

- Set the cluster subscription using the command shown in the portal (it will look something like this):
	```
	az account set --subscription 'subscribtion-id'
	```

- Copy the command shown in the portal for configuring `kubectl` (it will look something like this):
	```
	az aks get-credentials --resource-group AlgonquinPetStoreRG --name AlgonquinPetStoreCluster
	```

- Run the following command to apply the YAML configuration and deploy the application to AKS:
	```
	kubectl apply -f aps-all-in-one.yaml
	```

- Run the following command to apply the YAML configuration and deploy the application to AKS:
	```
	kubectl apply -f admin-tasks.yaml
	```

- Run the following command to apply the YAML configuration and deploy the application to AKS:
	```
	kubectl apply -f config-maps.yaml
	```

- Run the following command to apply the YAML configuration and deploy the application to AKS:
	```
	kubectl apply -f secrets.yaml
	```


- Confirm that all services are up and running:
	 ```bash
	 kubectl get services
	 ```


## Reflection Questions
    
---

## Challenges and Learnings (Optional)


---

## Acknowledgments

[Optional: Credit any resources, documentation, or people who helped you]
