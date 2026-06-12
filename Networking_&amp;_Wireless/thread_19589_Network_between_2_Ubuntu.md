---
title: "Network between 2 Ubuntu"
date: 2005-03-12
forum: Networking &amp; Wireless
---

### Post by Keito on 2005-03-12
Hi, 
I'm french and don't speak english very ( because I'm 14 years ) but I'll try.
So, I want to do a network between my 2 Computers which have Ubuntu as OS but I don't know how to do. Nobody help me on another forum that I won't quote, so please, is there someone who can help me and write me a steb by step.

Notice :  

Adsl Speedtouch USB ====== (usb) PC1 xxxxxxxxxxxxxxx (cross RJ45) PC2

You can tell me if you want more information about my computer or other.
Thx a lot to everybody who will help me.

Notice : I've already search with some word as : "Network Ubuntu" "Network RJ45" "2 Computer on Ubuntu" but i don't find anything.

---

### Post by Keito on 2005-03-13
Nobody can help me ?

---

### Post by mseney on 2005-03-13
[QUOTE=Keito]Nobody can help me ?[/QUOTE]

I just think we need a little more information. 

1. What do you mean by Network 2 Ubuntu machines?
ex) One Sharing Files via NFS, Samba, or Apache?

2.List all your Networking Hardware
ex) Hubs, NICs, cat5 cable, etc.

3.Does the 2nd PC need the internet accessible?


* I gather that you have one machine connected to your ISP using USB and then on that same machine you have an RJ45 Ethernet Interface in which you used a Cross-Cable out to the 2nd PC. 

Is the below example what you want?
-------------------------------------------------------
Internet DSL Modem -> USB -> PC1 
PC1 eth0 -> RJ45 Cat5 Cross Cable -> PC2 eth0

Your going to have to do some interface configuration and if you want to have your PC1 act as a Gateway to the Internet then prob add a route for the eth0 interface to route from eth0 to usb. An easier approach for dual internet setup would be a hub, router, or switch. Hub being the cheapest. But remember this is still possible the 1st way using PC1 as the gateway for PC2.

---

### Post by az on 2005-03-13
Salut!

Internet connection sharing is called masquerading or Network address translation.  To share a connection, you also need to do dns masquerading.

You can install dnsmasq and ipmasq.  Shorewall (firewall) also does NAT (as does firestarter, I think)  You should look into that (shorewall-doc)

To do file sharing, look up nfs.  You can also use Samba.  You will have to install some other samba packages that are not installed by default (butincluded on the cd)

---

