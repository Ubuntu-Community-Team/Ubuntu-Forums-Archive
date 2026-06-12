---
title: "TV card not working: MSI VOX USB2.0 - Gutsy Gibbon"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by gljubej on 2007-11-24
Hello, my TVtime application says:

 Frames too short from em28xx
 Cannot open capture device /dev/video0

This my dmesg printout:

[  235.448000] usb 6-3: new high speed USB device using ehci_hcd and address 3
[  235.580000] usb 6-3: configuration #1 chosen from 1 choice
[  235.732000] Linux video capture interface: v2.00
[  235.800000] em28xx v4l2 driver version 0.0.1 loaded
[  235.800000] em28xx new video device (eb1a:2820): interface 0, class 255
[  235.800000] em28xx #0: Alternate settings: 8
[  235.800000] em28xx #0: Alternate setting 0, max size= 0
[  235.800000] em28xx #0: Alternate setting 1, max size= 1024
[  235.800000] em28xx #0: Alternate setting 2, max size= 1448
[  235.800000] em28xx #0: Alternate setting 3, max size= 2048
[  235.800000] em28xx #0: Alternate setting 4, max size= 2304
[  235.800000] em28xx #0: Alternate setting 5, max size= 2580
[  235.800000] em28xx #0: Alternate setting 6, max size= 2892
[  235.800000] em28xx #0: Alternate setting 7, max size= 3072
[  236.512000] saa7115 0-0021: saa7114 found (1f7114d0e000000) @ 0x42 (em28xx #0)
[  238.720000] tuner 0-0043: chip found @ 0x86 (em28xx #0)
[  238.720000] tuner 0-0043: type set to 37 (LG PAL (newer TAPC series))
[  238.720000] tuner 0-0043: type set to 37 (LG PAL (newer TAPC series))
[  238.720000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[  238.720000] tuner 0-0060: chip found @ 0xc0 (em28xx #0)
[  238.720000] tuner 0-0060: type set to 37 (LG PAL (newer TAPC series))
[  238.720000] tuner 0-0060: type set to 37 (LG PAL (newer TAPC series))
[  238.720000] tuner 0-0061: chip found @ 0xc2 (em28xx #0)
[  238.720000] tuner 0-0061: type set to 37 (LG PAL (newer TAPC series))
[  238.720000] tuner 0-0061: type set to 37 (LG PAL (newer TAPC series))
[  239.172000] registered VBI
[  239.260000] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[  239.260000] em28xx #0: Found MSI VOX USB 2.0
[  239.260000] usbcore: registered new interface driver em28xx


Please tell me what must i do to get the TV card working.
I am using Gutsy Gibbon.

Thank you in advance.

---

### Post by gljubej on 2007-11-24
anybody? please help me...

Does anybody know something about this?

---

### Post by gljubej on 2007-12-01
Oh come one, there must be someone who can help me with this...

---

### Post by fenian on 2007-12-01
I think you need to use the em2820 driver to get it to work.Info is [here.]("http://mcentral.de/wiki/index.php/Em2880#Installation")

---

