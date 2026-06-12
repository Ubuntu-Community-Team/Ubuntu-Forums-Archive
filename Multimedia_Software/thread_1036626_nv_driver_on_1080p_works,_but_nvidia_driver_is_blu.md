---
title: "nv driver on 1080p works, but nvidia driver is blurry"
date: 2009-01-11
forum: Multimedia Software
---

### Post by nosebreaker on 2009-01-11
I am actually trying to setup a LinuxMCE system, I have 0710 working now (sorta).  I am using a Panasonic TH-42PZ80U 1080p plasma TV instead of a monitor, connected over DVI -> HDMI.

Kubuntu works fine, it detected the monitor and everything is fine, it uses the "nv" driver by default.

LinuxMCE sees I am using a 8500GT, and it changes it to a nvidia driver, which works except it is blurry.  I mean I can't read text unless I blow it up to be huge, it seems as if pixels are missing, and there is overscan (there is none with the nv driver, it works perfectly with that one).

The problem is, I can't use any of the nifty graphics effects with just the NV driver, but I can't read the text with the nvidia one.  I tried downloading and using the latest nvidia driver from their site but it won't load X if I use it.  

Any idea how to get this working properly with 1080p with the nvidia driver?

---

### Post by nosebreaker on 2009-04-27
I found the fix for this, it was due to my plasma having a refresh rate so fast that the driver didn't think it was valid, so it was ignoring the EDID info.  So I commented out all lines that talked about a resolution, and anything to do with EDID, and then it worked fine.

---

