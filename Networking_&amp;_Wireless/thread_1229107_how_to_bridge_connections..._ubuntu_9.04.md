---
title: "how to bridge connections... ubuntu 9.04"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by hooless on 2009-08-01
Hey all, I need a little help about bridging my wireless internet card with my ethernet card, so that I can connect my 360 to the internet, because my internet is through the wireless. I tried the brctl command, and that didnt work. any help?

---

### Post by jonobr on 2009-08-02
hello

If your bridge , that is connecting the two interfaces on the same network together, then Im guessing you will most likely needs the bridge utils availble in synaptic

> bridge in Linux 2.4 or later. The Linux Ethernet bridge can be used
for connecting multiple Ethernet devices together. The connecting is
fully transparent: hosts connected to one Ethernet device see hosts
connected to the other Ethernet devices directly.
 What this means is that if one interface is 1eg 192.168.1.20 and the other is 192.168.1.50 then the bridge utils are required as they are all in the same network address segment

A bridge acts as a layer two device and doesnt route

If however, your going to two different addresses
ie 192.168.1.20 to 10.10.10.20
then you will need to set your system up as a router to router between the two networks.

My guess is your doing number 1

---

### Post by hooless on 2009-08-02
yea, i guess i am doing number one.

so how do I create a bridge between my wireless(internet, called ra0) and my ethernet port(to 360, called eth0). how would I use bridge-utils to create a bridge?

---

### Post by jonobr on 2009-08-03
[Here in the server guide]("https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html") they have such an example.
If you scroll down to where it indicates installing the bridge-utils it will walk you through it.

One thing to note, you do need to stop your networking for a period to get this going

---

### Post by hooless on 2009-08-04
um, well thanks, but I didn't really get all of that, I didn't understand what it meant. could you help me? thanks!

---

