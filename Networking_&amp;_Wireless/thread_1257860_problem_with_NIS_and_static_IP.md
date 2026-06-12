---
title: "problem with NIS and static IP"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by beaker15 on 2009-09-04
Hi

I'm setting up a NIS server in a test environment with just 2 PCs, one as the server, one as the client. They are both clean ubuntu installs with just updates applied and the nis package installed on both through synaptic. All config files seem to me to be correct.

The problem i have is that I boot up the server, which gets an address from DHCP and run ***/etc/init.d/nis start*** and the server starts up fine. Then if i change it to a static IP address and run the same command, i get an error like:

*Starting NIS Services

*binding to yp server
*.......
*.......
*.......
*.......
*.......
*.......
*.......                              [fail]


This is all before I've even booted up the client. Could this be related to nsswitch.conf?

I'm really stumped so any help on this is appreciated

thatnks

---

