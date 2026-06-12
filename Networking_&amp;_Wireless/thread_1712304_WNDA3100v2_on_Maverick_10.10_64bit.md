---
title: "WNDA3100v2 on Maverick 10.10 64bit"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by thale on 2011-03-22
Clean install, when ever I plug the usb wireless device in, it totally kills something in the OS somewhere. If I start the machine with out it plugged in I'm able to run ndisgtk just fine, and use lsusb. As soon as I plug it in, lsusb hangs and never recovers as well as ndisgtk.

Other usb devices work just fine, and continue to do so even after it's plugged in. I'm totally at a loss at this point, any suggestions?

---

### Post by thale on 2011-03-28
No idea's huh?

---

### Post by suessz on 2011-08-27
Same problem same wifi adapter but newer version of install

---

### Post by northd_tech on 2011-08-27
Can you tell us some more about your hardware by posting the output of the following terminal commands?

```
lspci -vvnn | grep etwork
lspci -vvnn | grep ther
sudo lshw -C network
lsmod
ifconfig
iwconfig
lsusb
```

---

