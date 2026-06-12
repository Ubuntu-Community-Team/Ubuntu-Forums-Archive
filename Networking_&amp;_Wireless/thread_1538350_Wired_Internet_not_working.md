---
title: "Wired Internet not working"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by utkarsh.sawant on 2010-07-25
Hi all,
 
I have installed Ubuntu on a new PC, and not able to run Internet on it. 
 
LAN card: RTL8111/8168B PCI Express Gigabit Ethernet Controller
 
I can see eth0 has IP 192.168.1.102, and able to ping linksys router 192.168.1.1.
 
Also same cable connection works for my Laptop with windows, so cable and internet is fine.
 
As this is new PC do I have to install ethernet card driver for ubuntu..? but I am able to ping gateway...so wat can be issue ?
 
Please advice and I can put cmd results if required.

---

### Post by naveen9885 on 2010-07-25
Hey bro I have the same issue. check the link [http://ubuntuforums.org/showthread.php?t=1537782](http://ubuntuforums.org/showthread.php?t=1537782) issue not at resolved .

---

### Post by dineshs on 2010-07-25
> As this is new PC do I have to install ethernet card driver for ubuntu..? but I am able to ping gateway...so wat can be issue ?
I think,
If you get reply for 
```
ping -c3 4.2.2.1
```but not for
```
ping -c3 www.google.com
```
then it is a DNS issue
To solve,
1.If you are using NM in automatic DHCP mode
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection - edit
select ipv4 
method-Automatic DHCP addresses only
DNS [COLOR="Blue"]4.2.2.1[/COLOR]
then click apply
2.If you are depending on /etc/network/interfaces,edit /etc/resolv.conf as follows
```
sudo gedit /etc/resolv.conf
```
Back up the file and edit it so that it contains
```
nameserver 4.2.2.1
```

---

