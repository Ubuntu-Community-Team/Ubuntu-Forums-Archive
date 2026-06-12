---
title: "java socket programming"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by manish411 on 2011-06-14
**java socket programming**             
                                                                I am trying to build a simple client server chatting application 
I am making a socketserver using
     ```

        int port = 50001;
 ServerSocket   server = new ServerSocket(port); 

```the application is ready to listen to clients.
on the client side I am making 
a socket using
 ```

     int port = 5001;
String servername = "localhost";
 Socket client=new Socket(servername,port); 

```I am able to fully work on my chat application if I am running 
both the client and server application on my laptop
now the Socket() constructor also takes as
public Socket(InetAddress object,int host)
1.How do I use this constructor if I want to connect to a computer where I have this server
running on ip address "192.168.1.2" on the LAN
2.What if I want to connect to the server on the gobal ip address "117.205.133.123" of the router
but with the internal ip address " 192.168.1.1" within the LAN

I know I have to configure my router to forward the request on port 5001 to the ip of my
laptop " 192.168.1.2"

---

