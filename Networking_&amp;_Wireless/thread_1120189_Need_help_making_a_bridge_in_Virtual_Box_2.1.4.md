---
title: "Need help making a bridge in Virtual Box 2.1.4"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by alfaro on 2009-04-08
Hey guys, 

need help.  I have U-8.04LTS and have Vista as a virtual machine in Virtual Box 2.1.4

What I need is to bridge the Vista Machine, so I can see the Vista VM from the internal network (other physical workstations) inside the office.

I found a lot of how-to tutorials regarding bridging on the web, but most of them were based on VBox 1.6.

Do you guys know how?

---

### Post by Jose Catre-Vandis on 2009-04-08
It all happens automagically with 2.1.4. In the settings for your Vista VM, go to Network and choose host interface (it should auto-select eth0 lower down). Boot up your VM and if dhcp is working OK on Vista, and you have a router in the office serving up IP addresses, it should find itself on the network and be accessible by others

---

