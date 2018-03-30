# Haproxy

  * HAPROXY stands for High Availability.
  * it is popular opensource software for tcp/http load balancer and to provide proxy solution.

  * ha proxy can install on linux, solaris and freeBSD

  * haproxy is used to improve performance&reliability of servers by distributing the work load between multiple servers.

## types of load balancing

### No load balancing
  * this is the simple env which can not provide load balancing & no redundancy.




### transport layer load balanceing 

  * this is also called layer 4 load balancing
  * used to load balance network traffic between multiple servers
  * based on IP range and port num



### application layer load balancing

  * this is called layer 7 load balancing 
  * used to load balance network traffic between multiple servers 
  * based on content of user requests


## haproxy terminology 

acl: access control list
backend
frontend



### Acl: Access Control List
    * used to verify condition and perform action
    * condition is combination of ACL with operator
    * supported Condition:if,unless,eq
    * supported operator AND,OR,Negate(!)



### backend

    * this is set of servers which receives forwarded requests from frontend.
    * two parameters contained by backend 
      * list of servers and ports
      * load balancing alg to use

eg: 
```
   backend appserver
         balance roundrobin
         mode http
         server app1 ip:80 check
         server app2 ip:80 check
```
### frontend
    * this define how requests should be forward to backend
    * contains
      * a.set of IP address and port
      * b.ACL's
      * c.backend rule which is already defined in backend

eg:
````
frontend webapp
  bing *:80
  default_backendappserver

frontend webapp
  bind *:80
  acl url_blogpath_beg/blog
  default_backendappserver
````

## Load balancing ALg

### round robin: one by one

   * Default algorithm
   * select server turn by turn

### least connection: depend on load

   * select server with less number of conn
   * recommended for longer sessions

## source : depend on user/sourceIP
   * select server based on user IP address

## sticksessions: continues connection
   * To connect same server for long session.
## healthcheck: to check server availability
   * To check server availability 
   * traffic can manage based on health check


### nginx 

   * full web server
   * complicated slower
   * works with windows
   * no admin console
   * only http layer 
   * good caching
   * native ssl


### haproxy

   * only load balancer
   * faster
   * only opensoure
   * admin console
   * tcp 4 and http 7
   * advanced routeing and load balancing
   * native ssl

