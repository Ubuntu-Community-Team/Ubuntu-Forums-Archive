---
title: "Help needed ith a Belkin N600db usb wireless"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by ruffwuk on 2011-10-16
I have Ubuntu 11.10 on a Dell WS 670 workstation and just bought a Belkin N60 0DB usb wireless adapter.  Ubuntu did not recognize the usb adapter.  LSUSB shows it is there. Can someone help me, I am clueless on how to install it.

I tried downloading ndisgtk, it picked up the driver from the Windows CD provided and says installed 'yes' and wheni reboot, still no wireless.  I did the modprobe command and nothing.

---

### Post by datz89 on 2011-11-12
I am having the exact same problem, and took the same steps as you. Can anyone please help?

---

### Post by kleve on 2011-12-01
another one.
I have a Belkin F7D4101 that doesn't want to work
It doesn't appear to even be recognised:
lsusb = ID 050d:615a Belkin Components.

I have tried following instructions for similar queries like
[http://ubuntuforums.org/showthread.php?t=1515747](http://ubuntuforums.org/showthread.php?t=1515747)
[http://ubuntuforums.org/showthread.php?t=1522815](http://ubuntuforums.org/showthread.php?t=1522815)
[http://ubuntuforums.org/showthread.php?t=1673151](http://ubuntuforums.org/showthread.php?t=1673151)
and installed Realtek RTL8192SU but no luck

thx

---

### Post by praseodym on 2011-12-01
Hi kleve,

its a Broadcom-USB chip, it only works with ndiswrapper. Driver attached.

To the others: Please show:

```
uname -a
lsusb
lsmod
iwconfig
rfkill list
```

---

