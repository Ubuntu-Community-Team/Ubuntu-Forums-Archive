---
title: "problem connecting to home router"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by akasza1 on 2009-10-07
i am having trouble connecting to my wireless router at home. my network card is working and can detect my (and my all my neighbors') routers. when i try to connect to it, the network icon on my panel shows that its working and then wont connect.

im running jaunty on a dell inspiron 15n

any advice or help would be appreciated.

---

### Post by sedawk on 2009-10-08
One the command line try "iwconfig" and check if everything
is fine (ESSID, KEY if any (key only visible when running
"sudo iwconfig"), Signal strength).

---

### Post by utnubuuser on 2009-10-08
Alternately, you could try installing wicd.  It's a different network-manager and seems to function quite well.
I've been running 8.04 since it was released, and recently the network-manager behaves the way you described, so I finaly switched to wicd and my wireless service has improved.

In Synaptic>>Wicd - automaticaly removes network-manager, then installs wicd

---

