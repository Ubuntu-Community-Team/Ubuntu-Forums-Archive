---
title: "error on multiple ip address on one interface"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by samirafk222 on 2011-04-25
[SIZE=2]i am running virtual box on my laptop[/SIZE]
[SIZE=2]i am going to creat multiple ip address on one interface >>eth0[/SIZE]
[SIZE=2]but when i am rununing /etc/network/interfaces restart the following output appear:[/SIZE]
[SIZE=2]reconfiguring network interface ...[/SIZE]
[SIZE=2]RTNETLINK answer: no such process[/SIZE]
[SIZE=2]SIOCDELRT :no such process[/SIZE]
[SIZE=2]plz help .thanks in advanced[/SIZE]
 
auto eth0
iface eth0 inet static
address 192.168.1.160
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
 
auto eth0:1
iface eth0:1 inet static
address 192.168.1.188
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
 
i read some forum but have a problem

---

