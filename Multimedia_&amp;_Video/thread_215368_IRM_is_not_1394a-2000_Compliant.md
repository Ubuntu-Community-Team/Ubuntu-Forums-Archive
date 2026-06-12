---
title: "IRM is not 1394a-2000 Compliant"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by Fire on 2006-07-13
I am trying to get my firewire card working right.  Maybe someone on here will have and Idea.. below is what I get when i do a grep 1394... it shows IRM is not 1394a-2000 compliant and I have no idea right now what to do about that.. 

all help is welcome...

Thanks

fire@UbuntuGaming:~$ dmesg |grep 1394
[17179579.080000] ieee1394: Initialized config rom entry `ip1394'
[17179579.692000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179579.692000] ohci1394: fw-host0: Unexpected PCI resource length of 1000!
[17179579.744000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[febfa 000-febfa7ff]  Max Packet=[2048]
[17179581.024000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000d1008034be06 ]
[17179597.460000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1 )
[17179597.460000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17201533.352000] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[008088000282f177 ]
[17201533.352000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17201533.440000] ieee1394: raw1394: /dev/raw1394 device initialized
[17201618.648000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17201618.648000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[008088000282 f177]
[17201767.972000] ieee1394: Current remote IRM is not 1394a-2000 compliant, rese tting...
[17201768.300000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[008088000282f1 77]
[17201768.300000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17201772.320000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17201772.324000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[008088000282 f177]
[17201777.648000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[008088000282f1 77]
[17201777.648000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17202242.284000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17202242.284000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[008088000282 f177]
[17202415.392000] ieee1394: Current remote IRM is not 1394a-2000 compliant, rese tting...
[17202415.724000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[008088000282f1 77]
[17202415.724000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17202440.708000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17202440.708000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[008088000282 f177]
[17203623.276000] ieee1394: Current remote IRM is not 1394a-2000 compliant, rese tting...
[17203623.604000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[008088000282f1 77]
[17203623.604000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17203628.572000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17203628.572000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[008088000282 f177]
[17203631.056000] ieee1394: Current remote IRM is not 1394a-2000 compliant, rese tting...
[17203631.384000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[008088000282f1 77]
[17203631.384000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17203832.492000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17203832.492000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[008088000282 f177]
fire@UbuntuGaming:~$

---

### Post by Fire on 2006-07-14
I was able using Kino to get things working where I can download video off of my Video Cam...  But I still get the IRM is not 1394a-2000 Compliant.  at the end it says Node Suspended.  Perhaps this doens't matter but I would think thas a bad thing.  Let me know if I am over reacting.. I am just thinking that I can get better performance out of this if I can figure out what these messages mean...

---

### Post by macmasterxiv on 2007-08-17
I'm pretty sure it's a bad thing, since I'm trying to use ip over 1394 and the network keeps sporadically dropping with those error messages.

---

### Post by macmasterxiv on 2007-08-17
After searching the web, this seems to be a problem when ieee1394 kernel stack dies, usually because there's an issue with it coming back up from a suspend/resume cycle. If you guys don't suspend your computers, then the problem might lie elsewhere, but for me this fits the bill.

---

### Post by rockinlinux on 2008-03-14
have you guys found a fix for this? im getting this error in dmesg (kino currecnt remote IRM is not 1394a-2000 compliant) in mandriva. i use ubuntu and everything works fine. but in mandriva i start to capture and program quits...any tips to get this to work would be great :)

---

