---
title: "Dell Latitude D500 Wireless not Found"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by jhoffman1986 on 2009-10-01
Installed Ubuntu 9.04 on my Dell, and now it can't see the wireless card.  It comes with an Intel Wireless 2100 card.  Not sure what I'm doing wrong, or how to enable/install, but this is EXTREMELY important for my work, and I'm confused about what to do.  Any help appreciated!!

---

### Post by chili555 on 2009-10-01
Please open a terminal and do:```
sudo modprobe ipw2100
sudo ifconfig eth1 up
```Now can you click the Network Manager icon and connect?

---

### Post by jhoffman1986 on 2009-10-01
Typed in the commands.  First one (modprobe) doesn't do anything that I can see a response to, just gives me a new prompt.

Second one gives me a "device not found" response (I'm assuming referring to eth1).

---

### Post by chili555 on 2009-10-01
> doesn't do anything that I can see a response to, just gives me a new prompt.That means, roughly, "OK, I executed your command and have no errors or warnings to report." That's a good thing.

May we please see:```
sudo cat /var/log/messages | grep ipw

```Thanks.

---

