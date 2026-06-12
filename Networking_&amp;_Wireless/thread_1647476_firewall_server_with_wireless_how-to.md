---
title: "firewall server with wireless how-to??"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by espo111 on 2010-12-17
I was wondering if anyone can help me achieve this:

I want to use ubuntu server as a firewall and then route to a linksys wireless router.

here is the setup I would like:

DSL modem -->ubuntu server PC --> wireless linksys router with Ethernet-->2 Ethernet PCs, 3 wireless laptops



can anyone point me in the right direction? 

thanks
-f

---

### Post by spiky001 on 2010-12-17
Dose the router not have a built in firewall?

---

### Post by espo111 on 2010-12-17
> **spiky001 said:**
> Dose the router not have a built in firewall?

yes it does, but i want to use ubuntu as the firewall

---

### Post by spiky001 on 2010-12-17
Ok I think you,ll find the firewall in router is better, Do you have a gui on the server If not then ufw is the firewall, or you can learn about iptables. There is a section in this link about half way down [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) . Are you going to be opening the server to the internet as in using ssh vnc etc if not then nothing is open to the internet not like Windows dose

---

### Post by iponeverything on 2010-12-17
if the linksys can dd-wrt, you would better of just using it.

If it does not, dropping the linux box between dsl and linksys is pretty painless and a good exercise. 

It could be configured as a transparent bridge or IP'ed box that forwards packets.

---

