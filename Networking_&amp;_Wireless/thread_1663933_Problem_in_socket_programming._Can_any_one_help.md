---
title: "Problem in socket programming. Can any one help"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by dwnlds on 2011-01-10
[PHP]Hello [/PHP][HTML]
Hi,
I am new to the socket programming. 
can any one tell me what is is the problem in server.c and client.c program.

Error i am getting is : "Network not reachable" during connect() function in client.c

Both server.c and client.c is shown below.
[/HTML]Server .c
[HTML]
/***********************************************/
#include<stdio.h>
#include<sys/types.h>
#include<sys/socket.h>
#include<stdlib.h>
#include<string.h>
#include<arpa/inet.h>
/* Loop Back Addr*/

#define SERVER_IPADDR 127.0.0.1        
#define DEFAULT_PROTOCOL 0
#define PORT_NUMBER 7891

main(int argc,char *argv[])
{
    int sfd;
    printf("Creating Socket file\n");
    sfd=socket(AF_INET,SOCK_STREAM,DEFAULT_PROTOCOL);            /*Step 1 socket file creation.*/
     if(sfd==-1)
    {    perror("Unable to creat server socket file:");
        exit(1);
    }
    printf("Binding the socket file\n");
    struct sockaddr_in ser;                            /*Step 2: Initializing the socket file*/
    ser.sin_family=AF_INET;                            /*      binding the Port number and IP Address of server*/
//    ser.sin_port=htons(atoi(argv[1]));
    ser.sin_port=PORT_NUMBER;    //htons(PORT_NUMBER);
    ser.sin_addr.s_addr=inet_addr("SERVER_IPADDR");

    printf("PortNumber: %d\n",ser.sin_port);

    if(bind(sfd,(struct sockaddr *)&ser,sizeof(ser))==-1)
    {    perror("Change port address:");
        exit(2);
    }

    printf("Listen initializing the socket file");
    listen(sfd,10);                                /*Step 4: Listening the Clients */
    int    l,cli_fd;
    struct sockaddr_in cli;
    l=sizeof(cli);
    printf("Accepting the clients");
    cli_fd=accept(sfd,(struct sockaddr *)&cli,&l);                /*Step 5: Accepting the clients*/    
    
    printf("Client IP Addesss: %s\n",inet_ntoa(cli.sin_addr));
    printf("Client Port Number:%d\n",ntohs(cli.sin_port));
    char buf[512];
    strcpy(buf,"Welcome to Server System");
    printf("Send the data client");
    write(cli_fd,buf,sizeof(buf));            /*Step 6: Transmitting Data to client*/
    int r=read(sfd,buf,sizeof(buf));
    write(1,buf,r);
    close(sfd);
    close(cli_fd);
    //return 0;
}
[/HTML]Client.c
[HTML]
#include<stdio.h>
#include<stdlib.h>
#include<arpa/inet.h>
#include<sys/types.h>
#include<sys/socket.h>


#define SERVER_IPADDR 127.0.0.1
#define PORT_NUMBER 7891

main(int argc,char **argv)
{
    printf("Socket file creation\n");
    int cfd;
    cfd=socket(AF_INET,SOCK_STREAM,0);
    if(cfd==-1)
    {
        perror("creation:");
        exit(1);
    }    
    struct sockaddr_in ser;
    //int l;
    ser.sin_family=AF_INET;
//    ser.sin_port=htons(atoi(argv[1]));
    ser.sin_port= PORT_NUMBER;    //htons(PORT_NUMBER);
    ser.sin_addr.s_addr=inet_addr("SERVER_IPADDR");
    //l=sizeof(ser);
    printf("Port Number: %d\n",ser.sin_port);
    int l=sizeof(ser);
    int r=connect(cfd,(struct sockaddr *)&ser,l);        //sizeof(ser));
    if(r==-1)
    {
        perror("Connection:");
        exit(1);
    }
    char buf[]="I am connected to you";
    write(cfd,buf,sizeof(buf));
    r=read(cfd,buf,sizeof(buf));
    write(cfd,buf,r);
    close(cfd);
}
[/HTML]

---

### Post by endotherm on 2011-01-10
that probably means that your server app is not running, and has not opened 7891.
please post back the output of 

```
netstat -ntlup
```

---

### Post by dwnlds on 2011-01-11
Output for client program
```

Socket file creation
Port Number: 7891
Connection:: Network is unreachable

```Output of netstat -ntlup
```

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1111/cupsd      
tcp        0      0 255.255.255.255:54046   0.0.0.0:*               LISTEN      4404/ser
tcp6       0      0 ::1:631                 :::*                    LISTEN      1111/cupsd      
udp        0      0 0.0.0.0:51002           0.0.0.0:*                           721/avahi-daemon: r
udp        0      0 0.0.0.0:68              0.0.0.0:*                           4060/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           721/avahi-daemon: r

```

Server Code is running and in listening state only. Second Line is the my server program.

---

### Post by endotherm on 2011-01-11
well if netstat shows your server program listening on [FONT=monospace]54046, then your client must make it's connections to 54046, not 7891. 
and why is it listening on 255.255.255.255 (a symbolic IP representing a broadcast on the "zero network" 0.0.0.0/0; eg: all the hosts in the world)? that shouldn't be, so far as I am aware. it should[/FONT][FONT=monospace] be [/FONT][FONT=monospace]listening [/FONT][FONT=monospace]on either 0.0.0.0 (listening to any client) or 127.0.0.1 (local connections only). either way, you cannot ever send a packet to 255.255.255.255:54046. the IP stack won't allow it.

[/FONT]

---

### Post by gmargo on 2011-01-11
Here is why your server is not working.  The same problems are in the client code as well.

Problem 1:
This pair of lines:
```

#define SERVER_IPADDR 127.0.0.1
ser.sin_addr.s_addr=inet_addr("SERVER_IPADDR");

```is not doing what you think.  You are actually passing the string "SERVER_IPADDR" to inet_addr(), not the string "127.0.0.1".  Which is an error that inet_addr() indicates by returning a -1.  That's why you were seeing the 255.255.255.255 address.  Just move the quotes up to the #define.

Problem 2:
You are setting the socket port without using the htons() function.  You have it commented out, just revert that.  That's why you were seeing port 54046 instead of 7891.
```

    ser.sin_port=PORT_NUMBER;    //htons(PORT_NUMBER);

```

---

### Post by endotherm on 2011-01-11
> **gmargo said:**
> Here is why your server is not working.  The same problems are in the client code as well.

Problem 1:
This pair of lines:
```

#define SERVER_IPADDR 127.0.0.1
ser.sin_addr.s_addr=inet_addr("SERVER_IPADDR");

```is not doing what you think.  You are actually passing the string "SERVER_IPADDR" to inet_addr(), not the string "127.0.0.1".  Which is an error that inet_addr() indicates by returning a -1.  That's why you were seeing the 255.255.255.255 address.  Just move the quotes up to the #define.

Problem 2:
You are setting the socket port without using the htons() function.  You have it commented out, just revert that.  That's why you were seeing port 54046 instead of 7891.
```

    ser.sin_port=PORT_NUMBER;    //htons(PORT_NUMBER);

```
though I am just a watcher on this issue, thank you. I am not a C dev, nor a sockets programmer (I tend toward higher level langagues), but I should have noticed that quoted var. your explanation was most enlightening.

---

### Post by gmargo on 2011-01-11
This gentleman provides client/server examples in Python, Perl, C, and Java for both udp and tcp; it's a good resource.

[http://www.prasannatech.net/2008/07/socket-programming-tutorial.html](http://www.prasannatech.net/2008/07/socket-programming-tutorial.html)

---

### Post by dwnlds on 2011-01-12
hi 
Thanks for all for your valuable reply but still not working. i doesn't understand.
Error is coming at write(1,.....) function in server code (i think). Below complete details given.

Executed as follows: output is same when executed using $sudo
> Step1: In Server terminal [HTML]$ ./ser
Creating Socket file
Binding the socket file
PortNumber: 54046
Listen initializing the socket file
Accepting the clients[/HTML]> Step2: In Seperate terminal[HTML]$netstat -ntlup
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:7891          0.0.0.0:*               LISTEN      6234/ser        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
udp        0      0 0.0.0.0:51002           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -   [/HTML]> Step3: In Client terminal
[HTML]
$ ./cli
Socket file creation
Port Number: 54046
[/HTML] In Server Terminal
[HTML]$ ./ser
Creating Socket file
Binding the socket file
PortNumber: 54046
Listen initializing the socket file
Accepting the clients
Client IP Addesss: 127.0.0.1
Client Port Number:38803
Send the data to client
Error in Writing to std bug: : Bad address
[/HTML]> Modified code is [COLOR=Red]**color bolded**[/COLOR]Modified Client.c
```
/*
    Name:    01_client.c
    Description:    Demo for client server communication using sockets
*/
#include<stdio.h>
#include<stdlib.h>
#include<arpa/inet.h>
#include<sys/types.h>
#include<sys/socket.h>


#define SERVER_IPADDR** [COLOR=Red]"127.0.0.1"[/COLOR]**
#define PORT_NUMBER [COLOR=Red]**"7891"**[/COLOR]

main(int argc,char **argv)
{
    printf("Socket file creation\n");
    int cfd;
    cfd=socket(AF_INET,SOCK_STREAM,0);
    if(cfd==-1)
    {
        perror("creation:");
        exit(1);
    }    
    struct sockaddr_in ser;
    //int l;
    ser.sin_family=AF_INET;
//    ser.sin_port=htons(atoi(argv[1]));
    ser.sin_port= [COLOR=Red]**htons(atoi(PORT_NUMBER));**[/COLOR]
    ser.sin_addr.s_addr=inet_addr(SERVER_IPADDR);
    //l=sizeof(ser);
    printf("Port Number: %d\n",ser.sin_port);
    int l=sizeof(ser);
    int r=connect(cfd,(struct sockaddr *)&ser,l);        //sizeof(ser));
    if(r==-1)
    {
        perror("Connection:");
        exit(1);
    }
    char buf[]="I am connected to you";

    r = write(cfd,buf,sizeof(buf));
   [B] [COLOR=Red]if(r<0)
    {
        perror("Error in Writing to Socket\n");
    }[/COLOR][/B]
    r=read(cfd,buf,sizeof(buf));
    [COLOR=Red][B]if(r<0)
    {
    perror("Error in Rading the socket file\n");
    }[/B][/COLOR]
    write(cfd,buf,r);
    close(cfd);
}
```Modifed Server.c
```

/*
    Name:        01_server.c
    Description:    Demo program for server-client communication using socket API.
*/

#include<stdio.h>
#include<sys/types.h>
#include<sys/socket.h>
#include<stdlib.h>
#include<string.h>
#include<arpa/inet.h>
/* Loop Back Addr*/

#define SERVER_IPADDR [COLOR=Red]**"127.0.0.1"**[/COLOR]        
#define DEFAULT_PROTOCOL 0
#define PORT_NUMBER[COLOR=Red] **"7891"**[/COLOR]

main(int argc,char *argv[])
{
    int sfd;
    printf("Creating Socket file\n");
    sfd=socket(AF_INET,SOCK_STREAM,DEFAULT_PROTOCOL);            /*Step 1 socket file creation.*/
     if(sfd==-1)
    {    perror("Unable to creat server socket file:");
        exit(1);
    }
    printf("Binding the socket file\n");
    struct sockaddr_in ser;                            /*Step 2: Initializing the socket file*/
    ser.sin_family=AF_INET;                            /*      binding the Port number and IP Address of server*/
//    ser.sin_port=htons(atoi(argv[1]));
    ser.sin_port=[COLOR=Red]**htons(atoi(PORT_NUMBER));**[/COLOR]
    ser.sin_addr.s_addr=inet_addr(SERVER_IPADDR);

    printf("PortNumber: %d\n",ser.sin_port);

    if(bind(sfd,(struct sockaddr *)&ser,sizeof(ser))==-1)
    {    perror("Change port address:");
        exit(2);
    }

    printf("Listen initializing the socket file\n");
    listen(sfd,10);                                /*Step 4: Listening the Clients */
    int    l,cli_fd;
    struct sockaddr_in cli;
    l=sizeof(cli);
    printf("Accepting the clients\n");
    cli_fd=accept(sfd,(struct sockaddr *)&cli,&l);                /*Step 5: Accepting the clients*/    
   [COLOR=Red] [B]if(cli_fd==-1)
    {
        perror("Error in Accepting: ");
        exit(3);
    }[/B][/COLOR]    

    printf("Client IP Addesss: %s\n",inet_ntoa(cli.sin_addr));
    printf("Client Port Number:%d\n",ntohs(cli.sin_port));
    char buf[512];
    int r;
    strcpy(buf,"Welcome to Server System");
    printf("Send the data to client\n");
    r= write(cli_fd,buf,sizeof(buf));            /*Step 6: Transmitting Data to client*/
  [B][COLOR=Red] if(r<0)
    {
        perror("Error in Writing to Socket file: ");
        printf("\n");
    }[/COLOR][/B]
    r=read(sfd,buf,sizeof(buf));
    
    r= write(1,buf,r);
   [COLOR=Red] [B]if(r<0)
    {
        perror("Error in Writing to std bug: ");
        printf("\n");
    }[/B][/COLOR]
    close(sfd);
    close(cli_fd);
    //return 0;
}

```

---

### Post by gmargo on 2011-01-12
Line 66 of server.c
```

    r=read(sfd,buf,sizeof(buf));

```Wrong file descriptor. (And no error check.)

---

### Post by dwnlds on 2011-01-13
ya its true. Wrong File Descriptor.

And also in, client.c, last write sys call it is **1** not **cfd**.

Problem solved.

Thanks to all gmargo and endotherm.:D:popcorn:

---

