---
title: "No Wireless Intel/Pro 2200 Failed Firmware"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by SBFree on 2012-02-04
I have a laptop that uses an (R) PRO/Wireless 2200 adapter. It appears I have not loaded the firmware. The install is an Ubuntu based Backtrack 5 R1.

I get:
root@bt:~# dmesg | grep ipw
[ 11.048640] libipw: 802.11 data/management/control stack, git-1.1.13
[ 11.048646] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 11.205325] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[ 11.205331] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[ 11.205475] ipw2200 0000:06:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 11.205511] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[ 11.500939] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[ 11.500948] ipw2200: Unable to load firmware: -2
[ 11.500953] ipw2200: failed to register network device
[ 11.501003] ipw2200 0000:06:06.0: PCI INT A disabled
[ 11.501062] ipw2200: probe of 0000:06:06.0 failed with error -5

There is a similar thread
[http://ubuntuforums.org/showthread.php?t=1377887](http://ubuntuforums.org/showthread.php?t=1377887)
but it has a different error so I am not quite sure how to proceed. Any suggestions would be appreciated

---

### Post by hansdown on 2012-02-04
Hi, SBFree.

There was a bug reported, when the kernel version reached 2.6.15-17.

Not sure, if it was fixed.

---

### Post by SBFree on 2012-02-05
Thanks for the reply.
I kept surfing for a way to resolve this. Maybe this post will help others.
The firmware for this wireless card is not included.
It can be downloaded at:
[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)
unpacking and placing the file in:
/lib/firmware
seemed to resolve the problem.

Placing the folder with the firmware in /lib/firmware did not work. Placing the individual files there did.
Thanks again,
Scott

---

### Post by hansdown on 2012-02-05
Glad you fixed it, SBFree.

---

