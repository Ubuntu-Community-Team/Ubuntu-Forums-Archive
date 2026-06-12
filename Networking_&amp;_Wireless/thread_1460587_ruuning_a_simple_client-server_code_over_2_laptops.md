---
title: "ruuning a simple client-server code over 2 laptops joined by a cross-cable."
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by daudiam on 2010-04-23
Ubuntu 9.10. I have developed a DES encryption program in c++ and is using the following code to transfer it across 2 linux laptops connected by a cross cable. The code is working if I run the client and server programs on the same machine. But if I run the server program on another machine and on the client side, give the ip address of the other laptop, it says "Connection failed". 

I gave the ip address 10.31.0.10, subnet=255.255.0.0,gateway as 10.31.0.1 on the server computer. On the client side, I gave the ip address as 10.31.0.1 and gateway as 10.31.0.10 (opposite to the one on the server side) and typed the address 10.31.0.10 while executing the client code.  The code runs if I give localhost instead of the ip address (while running on the same computer). 

Also, if I ping 10.31.0.10 from the client side, it sends and receives packets normally. Also, it must be recognizing the server as there is also an option in the program which says "No such host" and that error is not getting shown. So its a networking problem, I assume.

The code for client is :

```
#include <iostream>
#include<cstring>
#include<cstdlib>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h> 
using namespace std;
void error(char *msg)
{
    cout<<msg;
    exit(0);
}

int main(int argc, char *argv[])
{
    int sockfd, portno, n;
    struct sockaddr_in serv_addr;
    struct hostent *server;

    char buffer[256];
    if (argc < 3) {
       cout<<"usage %s hostname port\n"<< argv[0];
       exit(0);
    }
    portno = atoi(argv[2]);
    sockfd = socket(AF_INET, SOCK_STREAM, 0);
    if (sockfd < 0) 
        error("ERROR opening socket");
    server = gethostbyname(argv[1]);
    if (server == NULL) {
        cout<<"ERROR, no such host\n";
        exit(0);
    }
    bzero((char *) &serv_addr, sizeof(serv_addr));
    serv_addr.sin_family = AF_INET;
    bcopy((char *)server->h_addr, 
         (char *)&serv_addr.sin_addr.s_addr,
         server->h_length);
    serv_addr.sin_port = htons(portno);
    if (connect(sockfd,(const sockaddr*)&serv_addr,sizeof(serv_addr)) < 0) 
        error("ERROR connecting");
    cout<<"Please enter the message: ";
    bzero(buffer,256);
    cin>>buffer;
    n = write(sockfd,buffer,strlen(buffer));
    if (n < 0) 
         error("ERROR writing to socket");
    bzero(buffer,256);
    n = read(sockfd,buffer,255);
    if (n < 0) 
         error("ERROR reading from socket");
    cout<<"\n"<<buffer;
    return 0;
}
```Its executed by [B]./a.out 5666

[/B]```
The server code is :
/* A simple server in the internet domain using TCP
   The port number is passed as an argument 
   This version runs forever, forking off a separate 
   process for each connection
*/
#include <iostream>
#include<cstdlib>
#include<cstring>
#include <sys/types.h> 
#include <sys/socket.h>
#include <netinet/in.h>
using namespace std;
void dostuff(int); /* function prototype */
void error(char *msg)
{
    cout<<msg;
    exit(1);
}

int main(int argc, char *argv[])
{
     int sockfd, newsockfd, portno, clilen, pid;
     struct sockaddr_in serv_addr, cli_addr;

     if (argc < 2) {
         cout<<"ERROR, no port provided\n";
         exit(1);
     }
     sockfd = socket(AF_INET, SOCK_STREAM, 0);
     if (sockfd < 0) 
        error("ERROR opening socket");
     bzero((char *) &serv_addr, sizeof(serv_addr));
     portno = atoi(argv[1]);
     serv_addr.sin_family = AF_INET;
     serv_addr.sin_addr.s_addr = INADDR_ANY;
     serv_addr.sin_port = htons(portno);
     if (bind(sockfd, (struct sockaddr *) &serv_addr,
              sizeof(serv_addr)) < 0) 
              error("ERROR on binding");
     listen(sockfd,5);
     clilen = sizeof(cli_addr);
     while (1) {
         newsockfd = accept(sockfd, 
               (struct sockaddr *) &cli_addr,(socklen_t*) &clilen);
         if (newsockfd < 0) 
             error("ERROR on accept");
         pid = fork();
         if (pid < 0)
             error("ERROR on fork");
         if (pid == 0)  {
             close(sockfd);
             dostuff(newsockfd);
             exit(0);
         }
         else close(newsockfd);
     } /* end of while */
     return 0; /* we never get here */
}

/******** DOSTUFF() *********************
 There is a separate instance of this function 
 for each connection.  It handles all communication
 once a connnection has been established.
 *****************************************/
void dostuff (int sock)
{
   int n;
   char buffer[256];
      
   bzero(buffer,256);
   n = read(sock,buffer,255);
   if (n < 0) error("ERROR reading from socket");
   cout<<"Here is the message: \n"<<buffer;
   n = write(sock,"I got your message",18);
   if (n < 0) error("ERROR writing to socket");
}
```Its executed on the same machine by **./a.out localhost 5666**

---

### Post by daudiam on 2010-04-24
I got it. The firewall was on. I just disabled it and it worked just fine after that.

---

