---
title: "load wifi module at startup"
date: 2011-09-05
forum: Networking &amp; Wireless
---

### Post by Eklips on 2011-09-05
Hi everyone,
I'm using Ubuntu 11.04,  After a couple day of hard working, I've manage to make my Asus n-13 usb wifi dongle to work properly.  The only thing that still bug me is that I have to unload/reload the module rt3070sta every time I reboot my computer.  It seems that the module hang on reboot.  The exact manipulation that I have to do each time is:
```

sudo ifconfig ra0 down
sudo rmmod rt5370sta
sudo modprobe rt5370sta
sudo ifconfig ra0 up
sudo iwconfig ra0 essid xxxxxx

```
I've try to put theses command in my rc.local but it dosen't seems to do anything
```

/sbin/ifconfig ra0 down
/sbin/rmmod rt5370sta
/sbin/modprobe rt5370sta
/sbin/ifconfig ra0 up
/sbin/iwconfig ra0 essid xxxxxx

```
Anyboy can fugure out why I have to unload/reload the module every time or show me how to execute theses comand at startup.

---

