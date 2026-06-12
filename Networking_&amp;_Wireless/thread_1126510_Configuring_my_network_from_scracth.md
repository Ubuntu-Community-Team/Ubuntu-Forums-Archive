---
title: "Configuring my network from scracth"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by DesignerX on 2009-04-15
Hi,

I managed to remove accedentily all my network interfaces including my ethernet interface. All I need is to connect to the internet through a router I have in my home. 

How do I reinstall my eth interface and connect to the internet ?

I have ubuntu 8.10

Thx alot.

---

### Post by DesignerX on 2009-04-16
All I need to do is just add a connection and I dont know how to do it. There was an Autoeth0 connection which i removed accidentally. There must be someone who knows how to do it.

thx.

---

### Post by celthunder on 2009-04-16
Go to network manager click hardware tab go to add new device and select ethernet type.

---

### Post by Yashiro on 2009-04-16
If you're not using networkmanager then

> sudo gedit /etc/network/interfaces

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

---

### Post by DesignerX on 2009-04-16
Thas exactly is my problem.
When I open the network manager I have only 3 options in the wired connections tabs : add, delete, edit.

When I try to add a connection I name it eth0 but I dont know how to configure it correctly so it will connect to the internet through my router which is WPA encrypted.

thx.

---

### Post by superprash2003 on 2009-04-16
set it up as shown by yashiro.. then type** sudo /etc/init.d/networking restart**

---

