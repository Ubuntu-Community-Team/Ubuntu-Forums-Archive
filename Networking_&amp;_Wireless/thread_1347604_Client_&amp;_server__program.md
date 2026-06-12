---
title: "Client &amp; server  program"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by ZuzooVn on 2009-12-06
Hi every one. I have a question for you. This code below is the Client & server progam which can be a simple chat program in Ubuntu.

Server.C: [http://paste.ubuntu.com/334989/](http://paste.ubuntu.com/334989/)
Client.C: [http://paste.ubuntu.com/334993/](http://paste.ubuntu.com/334993/)

Would you please tell me which the protocol (UDP, TCP) has been used in this code and show how some important code sections work :popcorn:

Thanks you very much

I look forward to hearing from you.

---

### Post by ibuclaw on 2009-12-06
Judging from this extract:
```
if((sockfd = socket(AF_INET, SOCK_DGRAM, 0)) == -1) 
```
You seem to use the protocol '**0**'

Comparing that to 'in.h' we get:
```
IPPROTO_IP = 0,   /* Dummy protocol for TCP */
```
Which is a TCP protocol, but that isn't very obvious in the code as you use the number, and not the enum that is assigned to that value.

Have a look here for a shorter version: [http://ubuntuforums.org/showpost.php?p=7400097&postcount=18](http://ubuntuforums.org/showpost.php?p=7400097&postcount=18)

Will probably tell you much more than what you currently have already.

Regards
Iain

---

### Post by ZuzooVn on 2009-12-07
Can it sent message between two computer :-?

---

### Post by ibuclaw on 2009-12-07
Yes, again - taking the example code you provided:
```

    /* get the host info */

    if ((he = gethostbyname(argv[1])) == NULL)

```
What this does is take the first argument and resolves the address to connect to.

So, for example, if your Server **hostname** was 'myserver', then you'd provide the argument **myserver.local**

Command line example:
```
./clientprog myserver.local "Hello World"
```

Regards
Iain

---

### Post by ZuzooVn on 2009-12-07
I run it successful in a computer. 
In one terminal, i type: ./receiver
In other terminal, i type ./sender 127.0.0.1 message  <127.0.0.1 : localhost >
./sender <hostname> <message>

And my problems here is:

I install Ubuntu 9.10 on **VMware Workstation**. I using my university's networks via HTTP proxy: Proxy and port: 8080.

Can u tell me, how can i find hostname in "sender **<hostname>** <message>"

Thank you very much

---

### Post by ibuclaw on 2009-12-07
2 ways of determining the hostname:

1) Look at the shell prompt - it will display in the format: USER@HOSTNAME:/PWD$
```
iain@**netbook**:~$
```
2) Use the following command:
```
hostname
```

Since the server you are trying to connect to is a VM, you will have to look up the documentation of that particular software on what IP/hostname is given to the guest OS.

Also, I doubt this will be a connection within your local network either, so you can probably ignore the ".local" bit.

Easiest way to think about resolver names though is to view it backwards.

ie:
```
myserver.local
```
is best thought as:
```
/local/myserver
```
and so any host under the /local tree can connect locally.

---

### Post by ZuzooVn on 2009-12-09
> **tinivole said:**
> 2 ways of determining the hostname:

1) Look at the shell prompt - it will display in the format: USER@HOSTNAME:/PWD$
```
iain@**netbook**:~$
```2) Use the following command:
```
hostname
```Since the server you are trying to connect to is a VM, you will have to look up the documentation of that particular software on what IP/hostname is given to the guest OS.

Also, I doubt this will be a connection within your local network either, so you can probably ignore the ".local" bit.

Easiest way to think about resolver names though is to view it backwards.

ie:
```
myserver.local
```is best thought as:
```
/local/myserver
```and so any host under the /local tree can connect locally.
In the same computer, It's the same result when i type: ./sender localhost or myserver.local or myip .
I check the if of  client and sever by type: ifconfig
I can ping each one from the other one.
But i still can't sent messages between them when i type: ./sender IpOfReceiver "Content"

---

