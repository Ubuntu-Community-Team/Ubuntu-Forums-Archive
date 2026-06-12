---
title: "LAN unknown IP addresses"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by molinus on 2010-12-23
Our single LAN network is 192.168.8/24, but after firing up our standalone Ubuntu Lucid Lynx Server and Samba, we have the following data using Netstat on a Mac:


Destination        Gateway            Flags    Refs      Use  Netif Expire
default            www                UGSc       13        2    en0
127                localhost          UCS         0        0    lo0
localhost          localhost          UH          1     1249    lo0
169.254            link#4             UCS         0        0    en0
172.16.98/24       link#7             UC          3        0 vmnet1
172.16.98.1        00:a7:14:c0:0d:21     UHLW        1   718014    lo0
172.16.98.254      00:a7:14:ec:6f:46   UHLW        0        6 vmnet1    440
172.16.98.255      link#7             UHLWb       2    71114 vmnet1
192.168.8          link#4             UCS        14        0    en0
192.168.8.1        a8:db:c7:67:53:b4  UHLW        0     9351    en0   1003

Does anyone know from where the 169 and 172 IPs might be originating?

---

### Post by WthIteh on 2010-12-23
> **molinus said:**
> 
172.16.98/24       link#7             UC          3        0 vmnet1
172.16.98.1        00:a7:14:c0:0d:21     UHLW        1   718014    lo0
172.16.98.254      00:a7:14:ec:6f:46   UHLW        0        6 vmnet1    440
172.16.98.255      link#7             UHLWb       2    71114 vmnet1

It seems that those IP addresses are coming from a VMWare software. See the vmnet1 there which is used by VMWare for naming its virtual interfaces.
It could be installed on anyone of your computers. You could check it by **traceroute** command too.

---

### Post by dandnsmith on 2010-12-23
[this site](http://www.jpsdomain.org/networking/nat.html) might be a useful reference. It shows the 'private' IP address ranges and more.

---

### Post by molinus on 2010-12-23
Thanks for the tip on VMware and great IP link! :D
That was definitely VMware's IP, and the link really helps clear up some other network issues.

Thanks again!

---

