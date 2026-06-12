---
title: "Another wireless card problem.  Its gone!"
date: 2006-01-13
forum: Networking &amp; Wireless
---

### Post by maddave on 2006-01-13
Hello.  I have been using Ubuntu on and off since end of last year.  It initially took my two days to get my wirless pcmia card up and running on my laptop.
Belkin card Broadcom 4306 chipset.

It was working up until last week.  I haven't used Ubuntu since then and I just booted it up.  There were lots of errors about the ndiswrapper not being able to load.  Something about version numbers no longer complient?!  And low and behold the card no longer works!

If I issue an ifup wlan0 command I get:
ifup wlan0
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0.

Dunno what to do?!!

Any help would be great!

---

### Post by maddave on 2006-01-13
Just to add to this. I reinstalled 1.7 version of ndiswrapper.

Installed it as directed.  When I did the modprobe ndiswrapper command I got the following error:
modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-6-386/misc/ndiswrapper.ko): Operation not permitted


So dont know what this means?!

Anywone?

---

### Post by Zelut on 2006-01-13
It sounds like an issue with the driver.. wireless can be very picky about the drivers under linux.  Have you recently upgraded the kernel or done any other major updates?  That could have caused the problem.

I can try to help you get this working again.. if you don't mind I'll PM you on the side and we can email out the solution.

---

### Post by Mr_Grieves on 2006-01-13
Perhaps the modprobe command demands sudo.
Try

```

sudo modprobe ndiswrapper

```

---

### Post by DerDon on 2006-01-27
Even if I don't have a laptop-wireless card, but a Belkin PCI (F5D7000), I have the same problem. 

"sudo modprobe ndiswrapper" is not a solution for me. 

Does anybody have another suggestion?

---

