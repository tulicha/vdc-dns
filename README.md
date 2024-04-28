# DNS Cluster

## Goals of this project

The goal of this project is to create authoritative DNS clusters. These clusters will be used to provide Domain Name System (DNS) services for the domain ".local." including reverse queries.

## Authors

- Adam Prchlík
  - Email: [adam.prchlik@example.com](mailto:adam.prchlik@example.com)

- Ondřej Slavík
  - Email: [slavion7@fit.cvut.cz](mailto:slavion7@fit.cvut.cz)

## Diagram of the project

![Diagram Of network](src/diagram.png)

## Diagram explanation

This project simulates a prutian approach for DNS in a larger company. 
It divides DNS servers into recursive (for serving users) and authoritative (for serving the domain(s) - in this case "*.local."). 
The assumption is that ordinary users will use recursive DNS servers to resolve queries for them. In this case, other services are hosted on these servers due to lack of machines.
The authoritative servers are located in the fail-over cluster. They are a much more critical infrastructure as they serve the domain(s) (*.local.) and can also be used as Slave Authoritative DNS for other organizations. 
If a computer in the cluster fails, the other server (VRRP -- keapalived) takes over its role.
In the event of a complete cluster failure, the second cluster will still serve the domain

## Documentation setup

# Authoritative cluster

- install all necessary packages: arping, traceroute, net-tools, keepalived, bind9
