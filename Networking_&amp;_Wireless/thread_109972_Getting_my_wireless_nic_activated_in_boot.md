---
title: "Getting my wireless nic activated in boot?"
date: 2005-12-29
forum: Networking &amp; Wireless
---

### Post by meistwer on 2005-12-29
Hi there,

I'm quite new in Linux and Ubuntu so my knowloedge is quite limited..;) 
I was wondering if there is a way of waking my wireless PCMIA NIC belkin f5d7010 during the booting process so I dont have to activate it every time I log on.

Cheers :razz: 


ROb

---

### Post by darth_vector on 2005-12-29
yes. edit the /etc/network/interfaces file as root and add a line like

auto ethx

where x is the interface number of the network card. it should then start up automatically.

---

### Post by Verbious on 2005-12-29
You might want to try adding the module to the start up.

How did you install the card?  Did you use ndiswrapper?

---

