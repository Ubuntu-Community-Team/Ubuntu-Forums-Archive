---
title: "keeping wired and wireless connections separate"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2009-04-13
My thin client server (Intrepid) is connected directly to my DSL modem (which has only one ethernet jack). I'd like to add wireless internet access for a laptop without any cross-connectivity to and from the wired network. Does it make sense to place a network switch between the modem and the server and then to connect a wireless router to a separate jack on the switch? Is there a better way to do it?
Thanks,
David

---

### Post by veloce on 2009-04-20
> **dbclinton said:**
> My thin client server (Intrepid) is connected directly to my DSL modem (which has only one ethernet jack). I'd like to add wireless internet access for a laptop without any cross-connectivity to and from the wired network. Does it make sense to place a network switch between the modem and the server and then to connect a wireless router to a separate jack on the switch? Is there a better way to do it?
Thanks,
David

If you want to control connectivity, then the best bet is a firewall.  If you can get an old pc (say: pentium, 128Mb Ram, 500Mb-1Gb disk - but you need three network cards) you could use purpose built distros (I use IPCop, pfsense is more powerful but more complex).  

You would connect the firewall to the internet, a cross over cable to your thin client server (using switch or cross over cable) and wireless router to the last network card.  In IPCop speak this is a red+green+blue setup.

---

### Post by NoJock on 2009-04-20
David: Hello the way that my system is set up is with Netgear wifi router it has Nat firewall built in it can be set to static ip for all by mac address filtering for assigning ip's to mac devices both on the wireless and wired side and it just works, it also will keep the assignmet to isp when it changes form the provider and all the assigned static ip's stay the same. This just works for my needs quit well.

---

### Post by dbclinton on 2009-04-21
> If you want to control connectivity, then the best bet is a firewall. If you can get an old pc (say: pentium, 128Mb Ram, 500Mb-1Gb disk - but you need three network cards) you could use purpose built distros (I use 
IPCop, pfsense is more powerful but more complex).

> You would connect the firewall to the internet, a cross over cable to 
your thin client server (using switch or cross over cable) and wireless router to the last network card. In IPCop speak this is a 
red+green+blue setup.

============

That is very interesting. I remember considering something similar when I was first setting up my network (at the time, the distro I was looking at was untangle), but I found that I could manage my wired network alone with sufficient precision through Safesquid. Now that I want to add a separate wireless net, this might do the job. 
Thanks!
David

---

### Post by dbclinton on 2009-04-21
> **veloce said:**
> If you want to control connectivity, then the best bet is a firewall.  If you can get an old pc (say: pentium, 128Mb Ram, 500Mb-1Gb disk - but you need three network cards) you could use purpose built distros (I use IPCop, pfsense is more powerful but more complex).  

You would connect the firewall to the internet, a cross over cable to your thin client server (using switch or cross over cable) and wireless router to the last network card.  In IPCop speak this is a red+green+blue setup.
I'll look into that too. Very helpful.
Thanks,
David

---

