---
title: "USB wifi antenna stops to work after few minutes"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by alain.roger on 2013-02-08
Hi,

i have a strange behavior with my USB wifi antenna. it use a RT3070L chipset and once it is connected it works very well, but if i don't use antenna for several minutes, it stops to work and i must switch it off and on to make it again usable....even if it's ON in gnome shell network window.

i would like to know if there is not an option (like under windows) to save energy that is ticked on...maybe this is the problem.

thx.

---

### Post by praseodym on 2013-02-08
Please show:
```

uname -a
lsusb
lsmod
iwconfig
sudo iwlist scan
rfkill list
```
I recommend pure WPA2-AES (CCMP) encryption and a fixed channel.

---

