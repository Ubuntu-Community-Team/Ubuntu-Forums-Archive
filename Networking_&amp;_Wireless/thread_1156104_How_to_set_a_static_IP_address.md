---
title: "How to set a static IP address"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Prince Valiant on 2009-05-11
I'm working on setting up a networked printer, and I can't figure out how to set a static IP address on the server that the printer is connected to.  Anyone able to tell me how?  Please bear in mind that I may not be able to understand everything you write. Thanks!

-Val

P.S.  I tried to follow [this]("http://www.jonathanmoeller.com/screed/?p=847") website's instructions, but I apparently don't have a file named "network."  Thanks!

P.P.S.  I'm running Ubuntu 8.10

---

### Post by Peter09 on 2009-05-11
If you are using a router the best place to set a static ip address is in the LAN area of your router. DHCP will still happen but the router will always deal the same ip to your machine.

---

### Post by superprash2003 on 2009-05-11
here's a way [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by chili555 on 2009-05-11
With all due respect to my esteemed colleague superprash 2003, if it's a server, it probably doesn't have or run a window manager and therefor Network Manager is not installed. I suggest editing /etc/network/interfaces to look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
```Restart the interface:```
sudo ifdown eth0 && sudo ifup eth0
```Substitute your details as needed.

Static IP implies that you, not the DHCP server, will handle the DNS name servers. I suggest that /etc/resolv.conf read like this:```
nameserver 192.168.1.254
```Let the router handle it for you.

Post back if you get stuck.

---

### Post by superprash2003 on 2009-05-12
correct.. my mistake..didnt notice the "server" part..

---

### Post by sahabcse on 2009-05-12
Follow below url for setting up the network

[http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html](http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html)

---

### Post by Iowan on 2009-05-12
Unfortunately, the instructions in the link you posted need some editing - the file is NOT /etc/interfaces/network - but (as in **chili555**'s example) /etc/network/interfaces.

Personally, I like the method known as a static lease. The DHCP server is configured (if it will handle it) to issue the same address to a machine based on it's MAC address. My laptop is currently failing to get a DHCP lease, so static lease won't work - but static address does.

---

### Post by Prince Valiant on 2009-05-13
Thanks for all the help!  I apologize to chili555, but I was wrong when I said I'm using a sever...it's the desktop version of Ubuntu 8.10 being used as a sever.  I used superprash's instructions successfully.  

-Val

---

### Post by Iowan on 2009-05-14
> **superprash2003 said:**
> correct.. my mistake..didnt notice the "server" part..As fate would have, that's probably a GOOD thing...

---

