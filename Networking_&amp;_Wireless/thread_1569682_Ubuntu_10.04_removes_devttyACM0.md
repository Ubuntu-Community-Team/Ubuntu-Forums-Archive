---
title: "Ubuntu 10.04 removes /dev/ttyACM0"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by rav0r on 2010-09-07
I am trying to use an ACM CDMA modem from Qualcomm (z010 from the romanian operator Zapp) on my ubuntu, but no ttyACM0 gets created as on my fedora or any linux system I used before. But there's more: I tried creating a ttyACM0 myself using mknod, but it automatically gets erased upon modem plug-in. I also tried creating an udev rule for this, which creates ttyACM0 upon plug-in and If I am quick enough, I can even querry the modem in the first  0.5 seconds, until the system removes ttyACM0 again. It is getting vrey annoing as I am missing the inspiration of how to prevent the system for doing this and why it is doing this.

---

