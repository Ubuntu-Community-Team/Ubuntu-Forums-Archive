---
title: "2 NIC problem"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by mvelicu on 2009-12-09
Hello !

I have a server UBUNTU 9.10. I Configured apache server, I created a web site,  I opened the port in router and forward to internal address, and test the web site with the [www.mydomain.ca](www.mydomain.ca) address. Everything run nicely and fast.
I put the second network card, I configurated it for other internal domain.I test the web site ,is not working anymore. If I test the web site on the internal network writing the ip address instead of [www.mydomain.ca](www.mydomain.ca) is working.If I write [www.mydomain.ca](www.mydomain.ca) is not working anymore.
The web site is working on the internal network for both addresses if I specify the ip addresses.

The both NIC's are configured with internal addresses as :


auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.111.25
netmask 255.255.255.0
network 192.168.111.0
broadcast 192.168.111.255
gateway 192.168.111.1


#The secondary network interface
auto eth1
iface eth1 inet static
address  192.1.1.6
netmask 255.255.255.0
network 192.1.1.0
broadcast 192.1.1.255
gateway 192.1.1.20



I configured the same but I put 2 Ip addresses on the first network card and I didn't configure at all the second card and is working just fine.
The problem is only when I configured 2 network cards.

What is the problem ?And how I can fix it ?

Thank you very much !
Mihai

---

### Post by mvelicu on 2009-12-09
I fixed  !

I deleted the second gateway and I added this line
at the end :

up route add default gw 192.168.111.1 dev eth0


Regards !
Mihai

---

### Post by Iowan on 2009-12-09
Congrats! You can mark the thread [SOLVED] by looking under Thread Tools - (last option?)

---

