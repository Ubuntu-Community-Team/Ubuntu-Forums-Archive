---
title: "D-Link DWA-125 disconnects"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by stembot on 2011-05-12
Wireless connects fine, then disconnects regularly.

I thought it might be an issue with the rt2870sta driver, so I blacklisted it, and it uses rt2800usb now:

```
[   13.625932] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   13.633139] usbcore: registered new interface driver rt2870
[   15.039402] <==== rt28xx_init, Status=0
[   15.992646] <==== rt28xx_init, Status=0
[  158.339701] <==== rt28xx_init, Status=0
[  278.340464] <==== rt28xx_init, Status=0
[ 3818.454594] <==== rt28xx_init, Status=0
[ 3978.559264] <==== rt28xx_init, Status=0
[ 4798.619302] usbcore: registered new interface driver rt2800usb
[ 4824.850590] <==== rt28xx_init, Status=0
[ 4998.593628] <==== rt28xx_init, Status=0
[ 5498.403411] <==== rt28xx_init, Status=0
[ 7218.359003] <==== rt28xx_init, Status=0
[ 9981.717499] <==== rt28xx_init, Status=0
[ 9982.777617] <==== rt28xx_init, Status=0
[10201.900447] <==== rt28xx_init, Status=0
[11024.395776] <==== rt28xx_init, Status=0
[11244.390883] <==== rt28xx_init, Status=0
[11324.381487] <==== rt28xx_init, Status=0
[11364.634246] <==== rt28xx_init, Status=0
[11464.394932] <==== rt28xx_init, Status=0
[12144.357259] <==== rt28xx_init, Status=0
[12264.633888] <==== rt28xx_init, Status=0
[12464.394894] <==== rt28xx_init, Status=0
[12724.414488] <==== rt28xx_init, Status=0
[12864.369764] <==== rt28xx_init, Status=0
[12970.530938] <==== rt28xx_init, Status=0
[12971.393951] <==== rt28xx_init, Status=0
[13292.433182] <==== rt28xx_init, Status=0
```


iwconfig:

```
wlan0     Ralink STA  ESSID:"xxxxxx"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 10:8C:CF:44:DA:C0   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-57 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

lsusb:

```
Bus 002 Device 005: ID 07d1:3c16 D-Link System 
```

I haven't found anyone with this specific issue with solutions.  

Any help is appreciated!

---

### Post by stembot on 2011-05-16
Guess I'm outta luck!  Awesome!

---

### Post by GSF1200S on 2011-06-21
> **stembot said:**
> Guess I'm outta luck!  Awesome!

Please see post #12 on this thread for my suggestion- we have the same wireless card too:

[http://ubuntuforums.org/showthread.php?t=1738030&page=2&highlight=DWA-125](http://ubuntuforums.org/showthread.php?t=1738030&page=2&highlight=DWA-125)

---

