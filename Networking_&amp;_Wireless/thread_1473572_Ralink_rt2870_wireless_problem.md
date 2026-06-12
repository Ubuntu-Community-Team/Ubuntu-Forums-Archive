---
title: "Ralink rt2870 wireless problem"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by chris0108 on 2010-05-05
I have just bought a ralink rt2870 usb wireless adaptor for my laptop, after a bit of playing around i managed (dont know how??) to get the device coming up as wlan2 but it wouldnt show any networks (with wicd manager) so i did a search around the forum and found a a thread about the same problem, i followed the guide but now i cant see the device at all, everything seamed to go well with no bad notices coming p whilst i followed the instructions.

lsusb output:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

iwconfig output:
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
(the ra0 has just reappeared??)

lsmod | grep rt output:

rt3070sta             503348  0 
parport_pc             31940  1 
parport                35340  3 ppdev,parport_pc,lp
agpgart                34988  2 drm,intel_ag

Thank you for any help Chris

Just a bit more info, i now have the wireless networks as veiwable, but when sat about two foot away fom my router it says i only got 23% signal??
It also tried to connect but can only come up with
"connected to 11n-AP at 10% (then gives the ip address)

---

### Post by eltonw on 2010-05-05
> **chris0108 said:**
> I have just bought a ralink rt2870 usb wireless adaptor for my laptop, after a bit of playing around i managed (dont know how??) to get the device coming up as wlan2 but it wouldnt show any networks (with wicd manager) so i did a search around the forum and found a a thread about the same problem, i followed the guide but now i cant see the device at all, everything seamed to go well with no bad notices coming p whilst i followed the instructions.

lsusb output:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

iwconfig output:
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
(the ra0 has just reappeared??)

lsmod | grep rt output:

rt3070sta             503348  0 
parport_pc             31940  1 
parport                35340  3 ppdev,parport_pc,lp
agpgart                34988  2 drm,intel_ag

Thank you for any help Chris

Just a bit more info, i now have the wireless networks as veiwable, but when sat about two foot away fom my router it says i only got 23% signal??
It also tried to connect but can only come up with
"connected to 11n-AP at 10% (then gives the ip address)

Would any of this help?:[http://ubuntuforums.org/showthread.php?t=1473629]("http://ubuntuforums.org/showthread.php?t=1473629")

---

### Post by chris0108 on 2010-05-05
Thank you for the reply, i have the most up to date drivers from ralink installed, it seams as though ubuntu doesnt like my router to be honest, two other laptops in the house running windows can connect and obtain automatic ip address and work fine, ubuntu just cant do this at all?

Its really strange cause this problem happened when i was using a belkin wireless pci card too.

Back to good old xp me thinks, its not good but it works

---

### Post by eltonw on 2010-05-05
> **chris0108 said:**
> Thank you for the reply, i have the most up to date drivers from ralink installed, it seams as though ubuntu doesnt like my router to be honest, two other laptops in the house running windows can connect and obtain automatic ip address and work fine, ubuntu just cant do this at all?

Its really strange cause this problem happened when i was using a belkin wireless pci card too.

Back to good old xp me thinks, its not good but it works

Kindly have a look at my recent post:[http://ubuntuforums.org/showthread.php?t=1473629]("http://ubuntuforums.org/showthread.php?t=1473629")

HTH...

---

### Post by ki4anr on 2010-05-05
Chris,

Please check out this forum thread it might be the answer you are looking for:

[http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070](http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070)

---

### Post by chris0108 on 2010-05-05
I have looked, im not running 10.4 (9.1) and the bottom link appears to go no where at all

---

