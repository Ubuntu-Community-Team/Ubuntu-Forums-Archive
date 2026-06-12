---
title: "ifconfig"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by seancis on 2009-10-27
When I use **ifconfig **I am given a hex number rather than an IP address. Only lo (localhost) shows the standard 127.0.0.1 ip. I tried using **sudo ifconfig eth0 down** followed by **up**, but I still see the same hex number. I researched the forums and tried **sudo /etc/init.d/networking restart** but still got the same hex number. How do I get an IP address to show instead of a hex number?

---

### Post by rippin on 2009-10-27
> **seancis said:**
> When I use **ifconfig **I am given a hex number rather than an IP address. Only lo (localhost) shows the standard 127.0.0.1 ip. I tried using **sudo ifconfig eth0 down** followed by **up**, but I still see the same hex number. I researched the forums and tried **sudo /etc/init.d/networking restart** but still got the same hex number. How do I get an IP address to show instead of a hex number?

What does your /etc/network/interfaces read?

---

### Post by oldfred on 2009-10-27
While you can do everything from ifconfig, it is easier just to use the gui.
Go to system, network connections, choose the eth0 or eth1 if shown or click add and set up there. If using dhcp click on the ipv4 setting and choose automatic dhcp.

The hex number you are seeing is just the mac address of you Ethernet card.

---

### Post by seancis on 2009-10-27
All I see is a command line - where can I find a system choice? (I am new to ubuntu) The hex addr is the inet6 addr; I'm not being shown an inet (v4) addr.

---

### Post by Iowan on 2009-10-27
I like the command line well enough - and would prefer to do some configuration that way... but I let Network Manager handle the connections where possible. Did you install the server version? Otherwise, you should have a desktop.

---

### Post by seancis on 2009-10-28
> **rippin said:**
> What does your /etc/network/interfaces read?
 
# The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by seancis on 2009-10-28
> **Iowan said:**
> I like the command line well enough - and would prefer to do some configuration that way... but I let Network Manager handle the connections where possible. Did you install the server version? Otherwise, you should have a desktop.
 
I didn't install ubuntu.  It was provided to me in a vmware image.  Once I start this image it boots into a command line.  I have a prompt in a vmware window; my mouse does not work in this window.

---

