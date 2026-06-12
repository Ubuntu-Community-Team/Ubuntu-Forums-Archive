---
title: "wireless device still not detected after installing ralink driver"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by sanlifaez on 2010-05-07
Just installed ubuntu 10.04 on packard-bell netbook xs20. out of the 8 distros i have tried, this is really the best, both in ease of installation and performance. I strongly recommend. 
the wireless however is a problem. i have given up installing the internal usb wireless (realtech) since it is only turned on by a touch key which is inaccessible in linux.

I am trying to install a wireless usb stick: sitecom wl-344 v1.
I am pretty sure its driver is ratlink's rt2870, that is even for windows.
i have installed the latest version of rt2870sta and it is loaded
```

bss@bss-netbook:~$ lsmod | grep rt2870
rt2870sta             554545  0
```but still i have no wireless device detected. 
```
bss@bss-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```I had the same problem after using ndiswrapper although device is reportedly present.

any clue where shall I start debugging?

i have already blacklisted rt2800usb

this might also help:
```

bss@bss-netbook:~$ modprobe -i rt2870sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```

---

