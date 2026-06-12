---
title: "Wifi refuses to complete handshake (Broadcom driver issues)"
date: 2011-12-13
forum: Networking &amp; Wireless
---

### Post by theyain on 2011-12-13
I have a Low Power, BCM4312 wireless card for my netbook and lately it has been giving me nothing but trouble.  It displays the local access points  but trying to connect to any of them, whether it be encrypted or not just doesn't work.  It use to do this when I would accidentally unplug the netbook.  After a recent kernel update the driver has refused to work at all.  Removing, purging, then re-installing the driver (b43) does nothing.  I can't use the STA driver because my card is black listed against it. If I do install the STA driver I get an error in the network applet that says 'firmware not ready'.

Here is some hopefully useful information


dmesg | grep b43
[http://pastebin.com/raw.php?i=hcube9b2](http://pastebin.com/raw.php?i=hcube9b2)

lspci | grep BC
[http://pastebin.com/raw.php?i=UkTxLxrw](http://pastebin.com/raw.php?i=UkTxLxrw)

Info from lshw
[http://pastebin.com/raw.php?i=8rBZH9PY](http://pastebin.com/raw.php?i=8rBZH9PY)

---

### Post by theyain on 2011-12-14
Bump?

---

