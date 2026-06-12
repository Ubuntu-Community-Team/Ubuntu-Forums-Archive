---
title: "Connect a PCMCIA ethernet card on a server install?"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by N8K99 on 2005-12-10
How do I get my laptop to see the Ethernet PCMCIA card on a basic server installation? I need to be able to access the internet to be able to perform a Low RAM Ubuntu installation.

---

### Post by Lambert on 2005-12-10
Little more info is needed.

Is the card recognized with a loaded driver? (is there output if you run iwconfig) 
What kind of card is it? make/model#

Run this command

sudo lshw -businfo

you should see the device. Notice it's class then run this command and post output here

sudo lshw -C <class>

where <class> = class of device minus the <>

---

