---
title: "Cannot access certain ports via web browser, outgoing port blocked?"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by kradnz on 2011-08-12
Hi, I am generally pretty good with finding solutions to thing like this but I have looked and it seems quite obscure. I am stumped.

I have a vps server running certain services which can be accessed via a web browser (e.g webmin control panel), but I have recently been unable to access these services from my home machine using Firefox 5.0, running ubuntu 11.04. 

Example: 

I can access the server on port 80 fine, eg: [http://myserver.com](http://myserver.com)

However I cannot access my webmin control panel on: [https://myserver.com:10000](https://myserver.com:10000)

The pages takes ages to load and then times out. Same with transmission-daemon on: [http://myserver.com:9091/transmission/web/](http://myserver.com:9091/transmission/web/)

Everything is set up fine on my server, the ports are open in firewall etc. and I can access these pages fine from my work computer.

This has only started happening in the last day or two and had been working fine up till then. I have not messed around at all with the firewall on my home machine. I have tried other browsers besides Firefox with same result.

Anyone got any ideas of what's going on?

---

### Post by kradnz on 2011-08-12
Output of ```
iptables -L


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by carverj on 2011-08-12
What happens when you run a trace using port 80 as parameter and then say 10000?

---

### Post by kradnz on 2011-08-12
Using tracepath?

```
root@shiva:~# tracepath xxx.xxx.xxx.xxx/80
 1:  shiva                                                 0.132ms pmtu 1500
 1:  DD-WRT                                                1.495ms 
 1:  DD-WRT                                                1.349ms 
 2:  192.168.1.20                                          3.420ms 
 3:  no reply
 4:  no reply
 5:  no reply
 6:  no reply
```

And 

```
root@shiva:~# tracepath xxx.xxx.xxx.xxx/10000
 1:  shiva                                                 0.120ms pmtu 1500
 1:  DD-WRT                                                1.354ms 
 1:  DD-WRT                                                1.358ms 
 2:  192.168.1.20                                          3.067ms 
 3:  no reply
 4:  no reply
 5:  no reply
 6:  no reply
```

192.168.1.20 is my gateway

---

### Post by kradnz on 2011-08-13
So I have worked out what is going on. I had to install traceroute. Here is what happens if I run a trace on port 10000:

> justin@shiva:~$ sudo traceroute -T -p 10000 myserver.com
traceroute to myserver.com (xxx.xxx.xxx.xxx), 30 hops max, 60 byte packets
 1  DD-WRT (192.168.2.1)  1.526 ms  1.881 ms  2.449 ms
 2  192.168.1.20 (192.168.1.20)  9.668 ms  10.994 ms *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *

It stops at my gateway router which is controlled by my ISP. Traces using ports 80,22,etc. go through fine. I believe that my ISP has probably blocked a whole lot of ports in response to new "Anti-copyright" legislation which was written by US corporations and passed into law by the New Zealand government last week. This makes sense considering that the ports have been blocked since the last couple of days.

I have implemented a workaround using ssh tunneling. So as a big screw you to the naive government and foreign corporations here is my workaround in case anyone else ends up in my predicament:

First set up passwordless ssh login to your remote server using ssh-keygen and ssh-copy-id for the sake of convenience.

I then set up a script to create the tunnels quickly and painlessly:
 
```
#! /bin/bash
ssh -NfC -L 9091:localhost:9091 user@myserver.com
ssh -NfC -L 10000:localhost:10000 user@myserver.com
```

---

