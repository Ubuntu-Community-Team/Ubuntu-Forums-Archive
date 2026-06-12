---
title: "Analyzing network crash ?"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by southof40 on 2012-08-03
I'm running 12.04 server as a guest of VirtualBox. The whole setup is only 48 hours old so I'm feeling my way a little bit.

Everything was working fine and then without any obvious reason both my ssh (PuTTY) and PgAdminIII sessions locked up at the same moment and were unable to reconnect. 

From within the Virtualbox console I was able to launch lynx and fetch webpages. 

After I did a ifdown followed by a ifup everything went back to normal.

I'm curious what happened - what log should I look in to see what Ubuntu thought happened ?

FWIW since the last reboot I had amended eth0 so that it went from a DHCP ip address to a fixed one but this took effect and everything worked for more than 24 hours before the incident I'm describing here.

---

### Post by southof40 on 2012-08-04
Hmm OK. Since that first post it's done it again. Little more concerned than I was before  :?

---

