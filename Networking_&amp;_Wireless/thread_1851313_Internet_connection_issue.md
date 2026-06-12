---
title: "Internet connection issue"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by mjonutz on 2011-09-28
Hello, this days i have installed ubuntu server 11.04 edition 64 bits. After i have finish the installation and i set up a static ip 
address when i try the following command: ping google.com the following message appears: ping: unknown host google.com.

/etc/network/interfaces -> iface eth0 inet static
the eht0 is configured to static with all the necessary information from the ISP to the address, netmask, network, broadcast, gateway
and in /etc/resolv.conf i have nameserver gateway_ip
 
I must admin that i am a beginner, but please help me to find the solution to my internet connection to be up and running.

Thanks in advance!

---

### Post by SparTacux on 2011-09-28
Did you enter your DNS Servers when you set up the static details?

---

### Post by mjonutz on 2011-09-28
I believe not, but how to check if did or not, or how to enter the DNS Servers ?

I only have the ip for the DNS, and not the name of the server.

---

### Post by SparTacux on 2011-09-28
I've never used version 11.04. Currently using 10.04 LTS - in this version click on the network icon at top of screen and select edit connections. Choose manual setup then enter all necessary details. In DNS servers just type  IP's of DNS servers separated by a comma and click apply. You may have to do a disconnect and reconnect using auto eth0 to get it to work.

---

### Post by mjonutz on 2011-09-28
I don t have any gui, I am at the console.

---

### Post by shubham1 on 2011-09-28
try visting some other website and then report me

---

### Post by haqking on 2011-09-28
> **mjonutz said:**
> I don t have any gui, I am at the console.

is your server connected directly to the internet or behind a router ?

are you using a private IP on your LAN ? if so then your nameserver or DNS should likely be the address of your router ?

is this static IP one you got from your ISP ? if so then it goes on your internet facing device such as the router.

can you show the following

```
cat /etc/resolv.conf
```

```
ifconfig
```

and upload here

---

### Post by mjonutz on 2011-09-28
Is connected directly to the internet.
I don t use private IP on my LAN.
My IP is that the ISP give it to me.

cat /etc/resolv.conf

resolv.conf
nameserver 81.180.166.1


ifconfig

eht0 Link encap:Ethernet HWaddr 00:12:79:a5:0b:39
     inet addr:81.180.166.151 Bcast:81.180.167.255 Mask:255.255.254.0
     inet6 addr: fe80::212:79ff:fea5:b39/64 Scope:Link
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:5697 errors:0 dropped:1854 overruns:0 frame:0
     TX packets 34 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:467192 TX bytes:2594
     interrupr:25

---

