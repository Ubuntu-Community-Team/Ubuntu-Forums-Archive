---
title: "dvgrab rom1394_0 warning: read failed"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by handverbrennung on 2007-11-19
I want to capture a video from my minidv camcorder (jvc). I works perfectly some months ago, no it won't. I read at google that it worked for otehr users with 2.4 and they got thesame problem since 2.6. But no solution.

Here what it says:

root@mobilemoo:~# dvgrab
rom1394_0 warning: read failed: 0x0000fffff0000414
error reading config rom directory for node 0
Error: no camera exists

/var/log/messages says:

root@mobilemoo:~# grep 1394 /var/log/messages
Nov 19 13:20:34 mobilemoo kernel: [  831.940000] ieee1394: raw1394: /dev/raw1394 device initialized
Nov 19 13:20:43 mobilemoo kernel: [  840.160000] video1394: Removed video1394 module
Nov 19 13:22:58 mobilemoo kernel: [   24.504000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[c8000000-c80007ff]  Max Packet=[2]  IR/IT contexts=[4/8]
Nov 19 13:22:58 mobilemoo kernel: [   25.144000] ieee1394: raw1394: /dev/raw1394 device initialized
Nov 19 13:22:58 mobilemoo kernel: [   25.176000] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.
Nov 19 13:25:47 mobilemoo kernel: [  201.032000] video1394: Installed video1394 module


What can i do?

Best regards, Enno

---

