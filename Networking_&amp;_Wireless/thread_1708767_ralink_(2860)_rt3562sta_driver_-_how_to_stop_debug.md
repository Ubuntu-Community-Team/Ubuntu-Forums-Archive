---
title: "ralink (2860) rt3562sta driver - how to stop debug info? (theres so much)"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by interzoneuk on 2011-03-17
I'm using ralink drivers from

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

(RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592) - 2.4.1.1

It works o.k except I get a hell of a lot of logs (dmesg /var/log/syslog)

i.e:-

-------------------------------------------
Mar 8 16:50:00 morgan-desktop kernel: [ 3301.106270] MediaState is connected
Mar 8 16:50:00 morgan-desktop kernel: [ 3301.106303] ==>rt_ioctl_giwmode(mode=2)
Mar 8 16:50:00 morgan-desktop kernel: [ 3301.106320] ==>rt_ioctl_giwfreq 6
Mar 8 16:50:00 morgan-desktop kernel: [ 3301.106356] rt28xx_get_wireless_stats --->
Mar 8 16:50:00 morgan-desktop kernel: [ 3301.106361] <--- rt28xx_get_wireless_stats
Mar 8 16:50:06 morgan-desktop kernel: [ 3307.103722] MediaState is connected
Mar 8 16:50:06 morgan-desktop kernel: [ 3307.103755] ==>rt_ioctl_giwmode(mode=2)
Mar 8 16:50:06 morgan-desktop kernel: [ 3307.103771] ==>rt_ioctl_giwfreq 6
Mar 8 16:50:06 morgan-desktop kernel: [ 3307.103808] rt28xx_get_wireless_stats --->
Mar 8 16:50:06 morgan-desktop kernel: [ 3307.103813] <--- rt28xx_get_wireless_stats
Mar 8 16:50:12 morgan-desktop kernel: [ 3313.107004] MediaState is connected
Mar 8 16:50:12 morgan-desktop kernel: [ 3313.107038] ==>rt_ioctl_giwmode(mode=2)
Mar 8 16:50:12 morgan-desktop kernel: [ 3313.107055] ==>rt_ioctl_giwfreq 6
Mar 8 16:50:12 morgan-desktop kernel: [ 3313.107092] rt28xx_get_wireless_stats --->
Mar 8 16:50:12 morgan-desktop kernel: [ 3313.107096] <--- rt28xx_get_wireless_stats
Mar 8 16:50:12 morgan-desktop kernel: [ 3313.107898] rt_ioctl_siwscan:: req.essid_len-9, essid-interzone
--------------------------------------

Anyone know how to stop the debug messages?

---

### Post by fcrvincent on 2011-03-29
Try the following command line:

iwpriv ra0 set Debug=0


Alternatively you could modify the Ralink driver wireless debug level in the rt_linux.c file (in os/linux/):

ULONG   RTDebugLevel = 0; // RT_DEBUG_TRACE;

and rebuild the driver (with make and make install)

---

### Post by Voilavoila on 2011-07-07
Thanks fcrvincent,

The command "iwpriv ra0 set Debug=0" removed (dynamically) the debug traces in /var/log/syslog.

Ubuntu 11.04 (64bits)

---

