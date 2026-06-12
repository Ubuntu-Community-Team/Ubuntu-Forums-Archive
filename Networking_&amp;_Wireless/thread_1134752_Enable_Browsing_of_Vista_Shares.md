---
title: "Enable Browsing of Vista Shares"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by reduxtion on 2009-04-23
I can currently connect to shares on Vista and on an Ubuntu server by adding a network place. My question is, how do I configure Vista so that I can browse through the shared folders in Dolphin? I see the workgroup, but the Vista system is not discovered.

Much thanks for any answer.

---

### Post by conorturton on 2009-04-23
Try this which I've just found works for me...

Open up terminal.

sudo gedit /etc/nsswitch.conf

Find the line that starts

hosts:     files  (etc)

Make sure that 'wins' follows files so it looks like:


hosts:     files wins (etc)

Mine looks like:

hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4

Click on Save then exit. Reboot.

---

