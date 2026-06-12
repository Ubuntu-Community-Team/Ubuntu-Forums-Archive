---
title: "How to Share internet to XP systems?"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by karthick87 on 2009-08-13
I am using ubuntu 9.04,n i have internet connection in ubuntu..now i want to share this internet connection to 3 of my XP systems..what are things required to do this??I am a beginner,so if someone say me step  by step..It will be great..

---

### Post by Iowan on 2009-08-13
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a starting point.

---

### Post by karthick87 on 2009-08-13
Great thank you...!But do i need two ethernet cards??

---

### Post by superprash2003 on 2009-08-13
yea , you would need two.. and you would need a hub/switch to connect the three xp machines to the ubuntu

---

### Post by karthick87 on 2009-08-17
I have two ethernet cards,this is my configuration
eth0 is assingned to dhcp and eth1 is assigned to the ipaddress
192.168.1.10
255.255.255.0
192.168.1.1

But i cant get the internet connection..Someone help..

---

### Post by superprash2003 on 2009-08-17
did you try link given by Iowan? post output of **ifconfig** from the terminal

---

### Post by tehchibipanda on 2009-08-17
Question about that guide.  Would that be the same steps needed to share my connection with my Xbox360?  Seeing as I do not want to pay how much they want for the little wireless adapter.

---

### Post by superprash2003 on 2009-08-18
yea , it would work

---

### Post by karthick87 on 2009-08-19
karthick@karthick-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:21:3a:ee:72  
          inet6 addr: fe80::224:21ff:fe3a:ee72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1460 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1378682 (1.3 MB)  TX bytes:253046 (253.0 KB)
          Interrupt:254 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:e0:42:c8:02:1c  
          inet6 addr: fe80::2e0:42ff:fec8:21c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:3127 (3.1 KB)  TX bytes:378 (378.0 B)
          Interrupt:16 Memory:fddff000-fddff0ff 

eth0:avahi Link encap:Ethernet  HWaddr 00:24:21:3a:ee:72  
          inet addr:169.254.7.7  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:254 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2658 (2.6 KB)  TX bytes:2658 (2.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:59.96.24.228  P-t-P:59.96.24.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:396676 (396.6 KB)  TX bytes:36088 (36.0 KB)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:59.96.27.42  P-t-P:59.96.24.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1291 (1.2 KB)  TX bytes:1331 (1.3 KB)

karthick@karthick-desktop:~$

---

### Post by Rootong on 2009-08-19
You can make your interface working in 8021q mode to avoid two network card.

---

### Post by karthick87 on 2009-08-19
After struggling for a long time,i have successfully shared my connection...But everytime i restart my system i have to re-enter all these commands again,how to solve it??

sudo iptables -A FORWARD -i eth0 -o eth1 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE

---

