---
title: "Totally confused. AE1000"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by styxxxola on 2011-03-31
So I am using Backtrack 4 R2 and have a linksys AE1000 usb wireless card. 

lsusb: Bus 001 Device 007: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]  

 So it recognizes it so I'm assuming it's supported.  

 locate ralink: 
/etc/modprobe.d/ralink 
/lib/firmware-2.6.35.8/LICENCE.ralink-firmware.txt 
/var/lib/dpkg/info/firmware-ralink.changelog 
/var/lib/dpkg/info/firmware-ralink.list  

 cat ralink: alias wlan* rt73  

 I have been searching through forums but all I'm finding are people who are installing it from scratch so I don't really know where to pick up. I am pretty new to linux. I know basic tasks and google is my best friend but I don't know the internals very well. 

  From what I'm finding after everyones finished installing, the command to have it run is: ifconfig ra0 up  

 ifconfig ra0 up ra0: ERROR while getting interface flags: No such device  I'm not really sure where to go from here.

---

### Post by dreadnot on 2011-09-18
I find myself in the same boat as Styxxxola. I , also, am very new to linux, and just have a very small experience with Terminal and linux command line codes. Same as well, lsusb sees my ae1000, and I have tried to follow every tutorial I have found....to no avail.

---

### Post by praseodym on 2011-09-18
Hello,

please show the terminal outputs of:
```

lsmod
iwconfig
rfkill list
```

---

