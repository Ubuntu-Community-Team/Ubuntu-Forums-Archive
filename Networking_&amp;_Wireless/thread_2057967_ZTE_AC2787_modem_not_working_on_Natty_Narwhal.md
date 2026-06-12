---
title: "ZTE AC2787 modem not working on Natty Narwhal"
date: 2012-09-14
forum: Networking &amp; Wireless
---

### Post by cinemaniac on 2012-09-14
I've bought a new High speed USB Modem and just can't get it to work on my laptop running Natty Narwhal. The modem is working fine under Windows. Would be great if anyone could help me with this. I've gone through dozens of blog posts and forum threads and tried many things but its a no-starter. There are quite a few threads that mention the same modem & the same provider as mine & they've gotten it to work through wvdial. However, in my case, usb-modeswitch is unable to switch it. I'm posting some information that I feel might be of help in understanding what I'm doing wrong.

1. Output of the wvdial command

```

xxx@ANDROMEDA:~$ sudo wvdial mts
[sudo] password for xxx: 
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

```

2. Output of the lsusb command
```

xxx@ANDROMEDA:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 19d2:fff5 ZTE WCDMA Technologies MSM 
Bus 003 Device 002: ID 0a5c:219c Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac8:c33f Z-Star Microelectronics Corp. Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

3. [Output of the dmesg command]("http://64.150.188.130/123d/dmesgout.txt")

4. [The usb-modeswitch log]("http://64.150.188.130/123d/usb_modeswitch_log.txt")

Please let me know if anything else would be required.

Thanks,

Sam

---

### Post by cinemaniac on 2012-09-15
Upgraded my kernel to the latest build & its working now. I still need to use the [sakis3g script]("http://www.sakis3g.org/") to 'prepare' the modem but even that wasn't working with the previous kernel build. The current kernel version is 2.6.38-16-generic.

---

