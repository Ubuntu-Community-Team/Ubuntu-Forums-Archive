---
title: "[SOLVED] Networking question."
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by Merovius on 2009-01-04
Here's my setup,

A Netgear wired router hooked to my broadband modem. 4 ports 3 hooked to 2 pc's and an Xbox. One is hooked to the WAN port of a ZyXel P-330 wireless router upstairs. Router upstairs has two pc's and a wireless laptop connected to it. (I believe it is in AP mode) All have internet acces just fine.

I have an Ubuntu PC downstairs and one upstairs. I cannot share anything between them. They do not see each other. It appears that the PC's downstairs can see each other and the same upstairs. But it's like I have two seperate networks that can't see each other.

I've tried Samba and Gnome-User-Share and Giver. What gives? Is it the two router thing? I figure it is. Any ideas welcome as I'm not a network genius by any standard. :confused:

TIA
Steve

---

### Post by zeronothing on 2009-01-04
ok I'm just trying to grasp the set here. you have two routers one of which is a netgear. then the second router is a ZyXel P-330. then you have one modem. now this is where I'm get lost, what is connected to what. obviously you have one of the routers connected to the modem from the routers WAN port to the modems port. Now from the other routers WAN port where do you have it plugged into? because this could be the problem. what might be the case is your devices are on sepreate subnets. one of the networks might be 192.168.0.1 255.255.255.0 and the other might be 192.168.1.1 255.255.255.0. this would case your PC not to see each other. what might help you is to check to see if you can use one of the routers as a switch instead of a router. some routers have that option with in the web interface used to configure the router.

---

### Post by Merovius on 2009-01-04
I have the wireless Zyxel hooked by it's WAN port into one of the Netgears lan ports. It provides wireless access for my daughter upstairs. 

Does this help?

---

### Post by Merovius on 2009-01-04
The addresses are exactly as described by zeronothing. Should they both be 192.168.0.1 to be on the same subnet?

---

### Post by Merovius on 2009-01-04
Well, I went ahead and switched the second router to Bridge mode as suggested and it seems to have mostly sorted things out. I can share files with Gnome-User-Share and managed to get the printer networked. I can see some of the windows PC's too. 

Thanks "zeronothing" for the help. :)

---

### Post by zeronothing on 2009-01-05
thats great you where able to set one of the routers to a bridge mode. So instead of having both routers trying to route traffic only one is doing it. Well, I guess that college ejamication really did work!!

---

