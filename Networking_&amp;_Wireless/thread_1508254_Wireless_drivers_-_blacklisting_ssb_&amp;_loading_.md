---
title: "Wireless drivers - blacklisting ssb &amp; loading wl"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by wildbluefaerie on 2010-06-12
I just had to format and reinstall my system, and just installed Ubuntu 10.04. I followed the instructions from [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) and got the driver for the Broadcom BCM4312 working without too much headache. But I can't get the module wl.ko to load at boot, and I can't get the ssb module to *not *load. I added ssb to /etc/modprobe.d/blacklist.conf and wl to /etc/modules but it doesn't seem to work. Every time I boot I have to do:

```

rmmod ssb
insmod wl
```Then after a few minutes, it starts working. I've been googling and searching the forums, but I can't figure out how to fix this. Could anyone point me to a thread or give me some direction here?

---

