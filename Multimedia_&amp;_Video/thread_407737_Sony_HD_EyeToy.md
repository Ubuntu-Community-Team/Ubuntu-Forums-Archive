---
title: "Sony HD EyeToy"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by Dodger73 on 2007-04-12
Hi all,

I've got a specimen of the Sony HD EyeToy (the PS3 version, SLEH 00201) attached to my computer and am trying to find a driver that works. The ov511 driver obviously doesn't (most likely a different sensor) - does anyone here have any experience with getting brand spanking new webcam hardware to function?  I'll be happy to provide logs and dumps and experiment with any combination of kernel modules :)   I could probably also take the camera apart to find out what sensor it's using...

---

### Post by Dodger73 on 2007-04-12
Here's some more info on the camera I managed to dig out:

USB Camera-B3.03.09.3:
 
Version: 1.00
Bus Power (mA): 100
Speed: Up to 480 Mb/sec
Manufacturer: OmniVision Technologies, Inc.
Product ID: 0x2000
Vendor ID: 0x1415

---

### Post by BobJelly on 2007-04-16
Hi!

I've got the same camera and I'm trying to make it work under Windows.

I opened mine, and found out it is using the OV0534-LB50.
See the following PDF for more details:
[http://www.ovt.com/data/imagepro/pdf/OV534-B88_PB%20(1.0).pdf](http://www.ovt.com/data/imagepro/pdf/OV534-B88_PB%20(1.0).pdf)

I've yet to find any driver for it...

---

### Post by Dodger73 on 2007-04-26
There's a collection of (Windows only) drivers at

[http://www.ovt.com/support/usbdownloads.asp](http://www.ovt.com/support/usbdownloads.asp)

They don't seem to work for me, however.

---

