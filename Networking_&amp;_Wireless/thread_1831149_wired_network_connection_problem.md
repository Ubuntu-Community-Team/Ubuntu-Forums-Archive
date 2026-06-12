---
title: "wired network connection problem"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by domenx on 2011-08-23
strange thing happen here...my network show my internet connection being established but i cant connect to internet!!..i try to use the command :
sudo ifconfig eth0 down
sudo ifconfig eth0 up

but no error given..


here is my ifconfig, i m using ubuntu 11.04 version:

eth0      Link encap:Ethernet  HWaddr 6c:f0:49:74:88:a7  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fe74:88a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34504 (34.5 KB)  TX bytes:128799 (128.7 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


sorry i'm new to ubuntu,i have surf through several topic but i cant get a solution for that.. please help me if u know anything bout my problem..

---

### Post by lmarmisa on 2011-08-23
Type these commands and post the results:

```

ping -c3 -b 192.168.1.255
ping -c3 192.168.1.1
ping -c3 8.8.4.4
ping -c3 google.com

```

Please, try to use the CODE tags for the commands and results (click on the icon **#** of the editor).

P.S. Welcome to the forums. :-D

---

### Post by domenx on 2011-08-24
thx for replying,i also wondering how the others embed the code tag..haha, so here is the code:


ping -c3 -b 192.168.1.255 :
```

WARNING: pinging broadcast address
PING 192.168.1.255 (192.168.1.255) 56(84) bytes of data.

--- 192.168.1.255 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

```


ping -c3 192.168.1.1 :
```

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=0.973 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=1.84 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=1.86 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 0.973/1.559/1.863/0.417 ms

```


ping -c3 8.8.4.4 :
```

PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Net Unreachable
From 192.168.1.1 icmp_seq=2 Destination Net Unreachable
From 192.168.1.1 icmp_seq=3 Destination Net Unreachable
--- 8.8.4.4 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2001ms

```


ping -c3 google.com :
```

ping: unknown host google.com

```

can u tell me the command
```
ping -c3 8.8.4.4 :
```
testing for what connection?  
i know the 192.168.1.1 and the 192.168.1.255 is testing for the lan network connection and google.com is for the internet network connection, am i right? correct me if i am wrong..
i am newbie here and trying to learn something so that next time if similar case occur i know how to deal with it..

---

### Post by lmarmisa on 2011-08-24
The problem could be external to Ubuntu.

The communications on your LAN seem good but the traffic to the Internet is not being routed.

Your last comments are correct.

Please, post the result of this command:

```

route -n

```

Three questions:

1) Do you have a router or modem on your LAN? I suppose that the IP address of this router would be 192.168.1.1.

2) Have you more equipments connected to your LAN?. If so, try to type a ping command to these equipments.

3) Are you able to connect to the internet from other computer or other operating system?.

P.S. The command **ping -c3 8.8.4.4** tries to check the internet connection with no DNS resolution.

---

### Post by aoaoo0 on 2011-08-24
> **lmarmisa said:**
> The problem could be external to Ubuntu.

The communications on your LAN seem good but the traffic to the Internet is not being routed.

Your last comments are correct.

Please, post the result of this command:

```

route -n

```

Three questions:

1) Do you have a router or modem on your LAN? I suppose that the IP address of this router would be 192.168.1.1.

2) Have you more equipments connected to your LAN?. If so, try to type a ping command to these equipments.

3) Are you able to connect to the internet from other computer or other operating system?.

P.S. The command **ping -c3 8.8.4.4** tries to check the internet connection with no DNS resolution.


This is absolutely correct, your computer can't connected to the outside, Should be routers configuration has problems([dll]("http://www.dllcure.com/"))

---

### Post by domenx on 2011-08-24
here the cpde for route -n:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
175.141.158.56  0.0.0.0         255.255.255.255 UH    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

1)i did have a modem connected and router ip is 192.168.1.1
2)i dun have any other equipment connected.
3)yup, i can connect to internet from other os.

---

### Post by lmarmisa on 2011-08-24
Is your computer a dual boot system with Ubuntu + Windows?.

Could you post the outputs of these commands?

```

traceroute -n -m1 8.8.4.4
traceroute -n -m2 8.8.4.4
traceroute -n -m3 8.8.4.4

```

Install **traceroute** if needed typing this command:

```

sudo apt-get install traceroute

```

---

### Post by e79 on 2011-08-24
```
ping -c3 google.com :
     
     ping: unknown host google.com 

```That leads me to believe you have _DNS problems (either misconfigured or inexistant)._

Could you post the result of **/etc/resolv.conf** please ?
```
cat /etc/resolv.conf
```

---

### Post by moonsal on 2011-08-24
Just a thought here... It helped me out quit a bit.... Make a new connection in NM.. Instead of Auto eth0 try manual and make a static ip... For instance, Ip = 192.168.1.105, Netmask = 255.255.255.0, Gateway = 192.168.1.1. . Assuming your routers Ip range is .100 - .149... Then log in to your router and check what your DNS servers are and add that to the DNS server line in NM.... Apply then open terminal and type the following..

```
sudo /etc/init.d/networking restart
```

This might not help ya maaan but it did me, after months of working with the same problem.....

---

### Post by domenx on 2011-08-24
_imarmisa _:

no, i am using wubi installation with windows.

when i was trying to use the command
**sudo apt-get install traceroute**

i get the following message:
```
Package traceroute is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'traceroute' has no installation candidate
```

d it means that i do anyting wrong when i installing ubuntu with wubi?


_e79_:

**cat /etc/resolv.conf :**
```

# Generated by NetworkManager
nameserver 192.168.1.1
```
anything go wrong with  my DNS?


_moosal_:
hmm...how to login to my router?sorry i am a noob here..

---

### Post by moonsal on 2011-08-24
```
firefox 192.168.1.1
``` then for login/pass enter admin/admin

---

### Post by lmarmisa on 2011-08-25
> **domenx said:**
> _imarmisa _:

no, i am using wubi installation with windows.

when i was trying to use the command
**sudo apt-get install traceroute**

i get the following message:
```
Package traceroute is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'traceroute' has no installation candidate
```

d it means that i do anyting wrong when i installing ubuntu with wubi?



What is your Ubuntu version?. Do not worry about your Ubuntu installation and the problem with traceroute.

Try to access to the router configuration menus using Firefox ( [http://192.168.1.1](http://192.168.1.1) ). You will need to know the user and password of your router. If you find a firewall function enabled, disable it. Sometimes this feature of the router is the cause of problems similar to yours.

A last question. I suppose that if you boot into Windows you have normal access to the internet. But if you boot into Ubuntu with Wubi, then the problem arises. Is that right?.

---

### Post by e79 on 2011-08-25
So your Ubuntu installation is set to look at your router to get DNS information, which is OK as long as your router has a DNS forwarder to whom it can speak when he doesn't know where to look....

I would suggest to look at your router configuration to make sure everything is ok as moonsal suggested.

---

### Post by domenx on 2011-09-06
sorry for late reply, i want to ask something here, not sure this 

will relate to this problem or not. Did configuration in window

will cause the problem to arise?if not, you can just simply
 
ignore this.

i have disable my IPV6 ip address in window,and also set all the DhcpConnForceBroadcastFlag flag to 0.are this the cause?



_imarmisa:_ 

my ubuntu version is ubuntu 11.04 desktop version.

yup, i can access my internet when i using window but cant access when using the ubuntu os.

_e79_:

i have try that, remake a new connection like what u have say,
but still the same case happen.i think maybe the problem is i was using a dynamic ip address, so did i need to switch my dynamic ip address to static ip address?if that the case, how to do it?please teach me with patient, thanks for your help!

---

