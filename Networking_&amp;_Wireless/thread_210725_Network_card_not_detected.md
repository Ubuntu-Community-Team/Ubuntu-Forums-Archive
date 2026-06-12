---
title: "Network card not detected"
date: 2006-07-07
forum: Networking &amp; Wireless
---

### Post by vodka on 2006-07-07
Hi All,

I've installed Kubuntu onto an old laptop to see if it might be suitable for our users. No problems at all. My network card was detected automatically. I configured the card and it connected to the LAN. I also wanted to check out the Ubuntu server version for our own internal use. The network card was not detected during installation of the server version... 
It's the same machine. 

It is an old laptop and the network card is a PCMCIA card. 
Is support for PCMCIA not included in the server version? 
Is there a way to manually install the network card?

Thanks in advance for any help.

---

### Post by vodka on 2006-07-07
Solved. 

During the setup I pressed "ctrl-f2" which took me to a console.
Typed "/etc/init.d/pcmcia start" and then went back to the setup (Ctrl-F1) and the network card was detected.

---

