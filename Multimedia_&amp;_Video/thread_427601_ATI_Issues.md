---
title: "ATI Issues"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by sowelie on 2007-04-29
Hey Guys,
I have been trying for weeks to get direct rendering enabled on my wife's machine.  I tried first with an ATI Radeon 9600 Pro and failed.  I am now trying with an X800 and running into the same issues.  It seems that it is an agp issue.  I am using the open source driver provided with feisty.  Here is the basis of my problem in my Xorg.0.log:

```
(EE) RADEON(0): [agp] Could not bind
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module.
```

Also, here is the agp information provided by dmesg:

[   35.982799] Linux agpgart interface v0.102 (c) Dave Jones
[   36.479861] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[   36.480540] agpgart: AGP aperture is 4M @ 0xe0000000
[ 7448.164855] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[ 7448.165051] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 7448.165257] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

I am really not sure where to start.  Any help is much appreciated.

---

### Post by Teroedni on 2007-04-29
it might be a bug in the driver.

IN xorg.conf
Try to change 

Option          "AGPMode" "4"

to

Option          "AGPMode" "1"

Just too see if that is the problem

---

### Post by sowelie on 2007-04-30
I feel so stupid!  I checked the BIOS settings before but I decided to give it one more check.  A combination of things was wrong.  First off the default video device was set to PCI.  Second, the Video Aperture size was set to 4MB!!! Now that I fixed these settings direct rendering works perfectly, no more errors, great framerate and beryl works.  Thank you for your help!

---

### Post by dodgePT on 2007-05-04
Which video aperture size did you choose by the way?

---

### Post by sowelie on 2007-11-24
Sorry about that, I didn't notice the reply.  You probably don't care anymore but for anyone reading this thread, I chose 256MB.

---

