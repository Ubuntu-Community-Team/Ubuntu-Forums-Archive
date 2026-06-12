---
title: "Other devices on network can see the server, but not access it."
date: 2013-04-18
forum: Networking &amp; Wireless
---

### Post by jca2323 on 2013-04-18
Hi.

I've recently run into trouble with my network server. It runs ubuntu 12.10. I cannot ping or ssh, or access the samba shares, but I can see the computer's samba shares from other devices. What I've noticed is that if the server has to connect to another device on the network (ex: pinging, lan games, etc.) I can then ssh into it, access samba shares, and ping it, but a little after the connection stops everything times out and doesn't work until I make another connection from the server. The server can access the internet and access the network. I have my router assign it a static ip address and it obtains that ip just fine. Nothing showing about connections dropping or anything.

Any help would be very appreciated.

---

### Post by jca2323 on 2013-04-18
> **jca2323 said:**
> Hi.

I've recently run into trouble with my network server. It runs ubuntu 12.10. I cannot ping or ssh, or access the samba shares, but I can see the computer's samba shares from other devices. What I've noticed is that if the server has to connect to another device on the network (ex: pinging, lan games, etc.) I can then ssh into it, access samba shares, and ping it, but a little after the connection stops everything times out and doesn't work until I make another connection from the server. The server can access the internet and access the network. I have my router assign it a static ip address and it obtains that ip just fine. Nothing showing about connections dropping or anything.

Any help would be very appreciated.

Update: If I ping a computer from the serverbI can ssh into it but then it drops the connection

---

### Post by jca2323 on 2013-04-19
Still no luck… anyone have any suggestions?

---

### Post by steeldriver on 2013-04-19
some kind of power management / acpi putting the interface hardware to sleep... ? maybe at the BIOS level?

---

### Post by jca2323 on 2013-04-19
That doesn't seem to be the problem as I could be troubleshooting at the server and cant remotely ssh into it when I try to ping it from  a Windows Machine I get this: 
[IMG]http://s22.postimg.org/d1whdgdup/image.png[/IMG]

---

### Post by jca2323 on 2013-04-20
Anyone have any suggestions as this is a major problem.

---

