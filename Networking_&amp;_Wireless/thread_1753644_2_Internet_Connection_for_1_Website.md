---
title: "2 Internet Connection for 1 Website"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by mrshaheer2000 on 2011-05-09
Dear all



I am mess up in NIC configuration.

I have only one web site on my server.

I Have 2 Internet connection with static IP. 

I have 2 Network Card as follow
    eth0 119.155.152.140 (1st internet with static IP without firewall) 
    eth1 203.135.30.240 (2nd internet with static IP without firewall)


when i restart my networking it give me following error

```

shah@server:~$ sudo /etc/init.d/networking restart
[sudo] password for shah: 
* Reconfiguring network interfaces...          
RTNETLINK answers: No such process
                                                                         [ OK ]
shah@server:~$ 


```


Here is my network interfaces configuration

```

shah@server:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 119.155.152.140
        netmask 255.255.255.0
        gateway 119.155.152.1


auto eth1
iface eth1 inet static
	address 203.135.30.240
	netmask 255.255.255.0
	gateway 203.135.30.1
shah@server:~$ 

```

Is my network interfaces configuration is correct?

I registered my these IP to Domain Registrar but still my web site not online.

Please advice me what should i do?

NOTE: I dont have DNS or DHCP server installed.


Regards

Shaheer]

---

### Post by mrshaheer2000 on 2011-05-10
anybody!

help me please :(

---

### Post by lz1dsb on 2011-05-10
If this is a Web Server than those addresses should be reachable from the public Internet address space. Here's what I get when I try to reach them:
boyan@boyan-virtual-machine:~$ ping 203.135.30.240
PING 203.135.30.240 (203.135.30.240) 56(84) bytes of data.
64 bytes from 203.135.30.240: icmp_req=1 ttl=47 time=221 ms
64 bytes from 203.135.30.240: icmp_req=2 ttl=47 time=224 ms
64 bytes from 203.135.30.240: icmp_req=3 ttl=47 time=222 ms
^C
--- 203.135.30.240 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 221.367/222.831/224.923/1.612 ms
boyan@boyan-virtual-machine:~$ ping 119.155.152.140
PING 119.155.152.140 (119.155.152.140) 56(84) bytes of data.

^C
--- 119.155.152.140 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 5999ms

So the second address is isn't responding to ICMP Echo Request packets, which doesn't mean necessarily that it's not reachable, it could be that the ICMP packet is blocked somewhere along the way. 
Trying to access port 80 on your server (the well known http port) gives me:
boyan@boyan-virtual-machine:~$ telnet 203.135.30.240 80
Trying 203.135.30.240...
Connected to 203.135.30.240.
Escape character is '^]'.
HTTP/1.1 400 Bad Request
Server: micro_httpd
Cache-Control: no-cache
Date: Sat, 01 Jan 2000 00:25:49 GMT
Content-Type: text/html
Connection: close

<HTML><HEAD><TITLE>400 Bad Request</TITLE></HEAD>
<BODY BGCOLOR="#cc9999"><H4>400 Bad Request</H4>
No request found.
<HR>
<ADDRESS><A HREF="http://www.acme.com/software/micro_httpd/">micro_httpd</A></ADDRESS>
</BODY></HTML>
Connection closed by foreign host.

Which means that the http port is open and there's a server that is handling my request (not successful in this case anyway). When I tried it in the browser I was asked for a username and password.
Doing the same for the other IP address:
boyan@boyan-virtual-machine:~$ telnet 119.155.152.140 80
Trying 119.155.152.140...

So the web service isn't available on that address.



Cheers

---

### Post by lz1dsb on 2011-05-10
I think that this is what you need:
[HTML]http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/[/HTML]


Cheers, 
Boyan

---

### Post by mrshaheer2000 on 2011-05-12
> **lz1dsb said:**
> I think that this is what you need:
[HTML]http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/[/HTML]


Cheers, 
Boyan

Dear Boyan

Since yesterday i am trying to understand this article/tutorial but because of lack of my iptables basics knowledge. It is making me tens.

would you please help me and give me exact solution with my own ips?


Regards

Shaheer

---

### Post by lz1dsb on 2011-05-18
Hi, 
I'll try to adapt it to your addresses. I wasn't able to test it though as I'm experiencing some issues with the Linux core I'm emulating. So let's start:
Short introduction. The whole idea is to have two different routing tables and for each routing table you'll have a different default gateway. And also we'll create a rule which will instruct the system which routing table to use. You already have a default routing table so we'll only need to create one more:
1. echo 1 Admin >> /etc/iproute2/rt_tables

The file /etc/iproute2/rt_tables should look like this:
#
# reserved values
#
255     local
254     main
253     default
0       unspec
#
# local
#
#1      inr.ruhep
1 Admin

Your IP configuration is:
auto eth0
iface eth0 inet static
        address 119.155.152.140
        netmask 255.255.255.0
        gateway 119.155.152.1


auto eth1
iface eth1 inet static
	address 203.135.30.240
	netmask 255.255.255.0
	gateway 203.135.30.1
So in this case remove the second Default Gateway 203.135.30.1, 
we'll put it into the newly created routing table:
ip route del default via 203.135.30.1
Then we'll add this default route to the new Admin routing table
along with another route:
ip route add 203.135.30.0/24 dev eth1 src 203.135.30.240 table Admin
ip route add default via 203.135.30.1 dev eth1 table Admin

Now it's time for the rules:
ip rule add from 203.135.30.240/32 table Admin
ip rule add to 203.135.30.240/32 table Admin

From the output of ip rule show you should see something like this:
from all to 203.135.30.240 lookup admin
from 203.135.30.240 lookup admin

And this should be it. Let me know if this helps.


Cheers, 
Boyan

---

### Post by lz1dsb on 2011-05-20
Any success on that?

---

### Post by mrshaheer2000 on 2011-06-02
Dear Boyan

Sorry for late reply.

I was in search of sold solution so that I found pfSense 

pfSense is awesome. 

I have successfully archive my goal.

you can check [http://www.pfsense.org/](http://www.pfsense.org/)

it is software based low cost solution of load balancing 

But I am very thankful to your co-operation in this regards

I love the way you help peoples.


Cheers :D

Shaheer

---

