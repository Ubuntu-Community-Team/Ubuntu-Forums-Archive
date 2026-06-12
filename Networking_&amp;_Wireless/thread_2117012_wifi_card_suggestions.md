---
title: "wifi card suggestions?"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by kr651129 on 2013-02-17
I'm running Ubuntu 12.10 x64 on my desktop.  It's running samba, openssh, tvheadend to provide video to my xbmc clients and a few other services.  The conectivity is a bit on the slow side, I'm currently using a USB Wifi device.  It being slow is fine but it my xbmc clients seem to hang when buffering the video and I'm gussing it's due to network speed.  I'd love to hardwire the connection but it's not possible.  Can anyone recomend a wifi card for my machine that they've had good luck with?

---

### Post by praseodym on 2013-02-17
What device do you use? Please show:
```

ifconfig -a
iwconfig
lsusb
lsmod
sudo iwlist scan
```

---

