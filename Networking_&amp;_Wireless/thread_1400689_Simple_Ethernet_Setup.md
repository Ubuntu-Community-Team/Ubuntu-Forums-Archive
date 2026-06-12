---
title: "Simple Ethernet Setup"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by ks07 on 2010-02-07
Hey,
I have an old pc currently running ubuntu server 9.10. It was configured during install to connect to the home wifi router by a PCI ethernet card, which worked all well and good. However, at the moment I cannot connect to the router (I have moved the machine too far from it). 

I want to connect this machine (desktop) to the server so I can SSH into the box and backup some files. I need help creating a simple wired network connection between the two, as I have no clue as to where to start.

---

### Post by Iowan on 2010-02-07
Does the server have a static IP address (or is/was it the DHCP server)? You will need a crossover cable or a hub/switch/router.

If the server has a static address and you have a crossover cable, you will need to configure "this machine (desktop)" with an address in the same subnet as the server. The server will need to have SSH-server installed.

---

### Post by ks07 on 2010-02-07
Ah that's where I've gone wrong. Been trying to use just a regular ethernet cable. I've got an old hub that I can use but it's in storage atm. I'll forget about this for now, it's far from urgent.

Thanks for the advice anyway :)

---

