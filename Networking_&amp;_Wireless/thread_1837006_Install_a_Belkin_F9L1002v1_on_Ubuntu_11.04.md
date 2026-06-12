---
title: "Install a Belkin F9L1002v1 on Ubuntu 11.04"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by alesmile on 2011-09-01
Hi everyone!  Recently I've installed Ubuntu 11.04 on my computer, so I'm new in this.  I'm trying to install a Belkin Wireless Usb Adapter but when I connect the device to computer nothing happens. The computer doesn't recognize  it.  I tried with some solutions that I saw in this forum but nothing works.

---

### Post by northd_tech on 2011-09-01
Will you post the results of the following Ubuntu terminal commands with the Belkin USB adapter plugged in at Ubuntu startup:

```
lsusb
sudo lshw -C network
lsmod
ifconfig
iwconfig
lspci -vvnn | egrep 'etwork|thernet|ireless'
rfkill list all
sudo iwlist scan
nm-tool
```

---

