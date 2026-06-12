---
title: "just bought  a new dell Inspiron E1705 and it will not detect the wireless network"
date: 2006-03-10
forum: Networking &amp; Wireless
---

### Post by davify on 2006-03-10
Hey you all am new to linux,I installed fedora on my new dell laptop inspiron E1705,but it will not detect the wiresless card,I do not know what else to do,if anyones knows what to do please help me out.I would love to install Ubuntu but I do not know whether this will work since this is  a new kind of laptop
asap

---

### Post by cyberchills on 2006-03-10
davify:  I assume the card is internal and not pcmcia correct?  If so start off by posting the results of `lspci`.  You should be looking for a Network line.  We can see if the network chip is supported based on this info.  I have a feeling that you will need to look at the ndiswrapper project for support at this time.
[http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by davify on 2006-03-10
hey everyone the model of the wireless I have
 is intel pro wireless 3945,A/G ,DC,19400/E1705

---

### Post by parry on 2006-03-21
davify: Check [IPW3945 Project Website ]("http://ipw3945.sf.net") - I have the same laptop and the OSS driver provide at the site works well for me.

---

### Post by jml on 2006-03-22
Another way of finding out if Ubuntu will work for you is to download the Live CD version of Ubuntu, burn the iso to a disc and boot it up.  If the Live CD version works with your wireless card, there is a very good possibility that the install version will work as well.  Not as sophisticared a solution as the other one listed, but I hope equally useful.

Joe

---

### Post by gnap on 2006-05-26
Have you solved the problem?

---

### Post by PhrankDaChickenGeek on 2006-05-26
[QUOTE=gnap]Have you solved the problem?[/QUOTE]

The beta version of Ubuntu - Dapper Drake, already supports the Intel 3945 chipset. Just download and install the latest 686 kernel and network-manager, and you should be good to go!

---

