---
title: "Not configured to drive a VGA console message?"
date: 2012-12-22
forum: Multimedia Software
---

### Post by dannyboy79 on 2012-12-22
I am getting this in my dmesg output, what does it mean? I am using Nvidia Binary driver 304.64 from the Additional Drivers dialog box.
I have a GeForce 8400GS 1GB DDR3.
```
[   32.029858] NVRM: Your system is not currently configured to drive a VGA console
[   32.029863] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   32.029867] NVRM: requires the use of a text-mode VGA console. Use of other console
[   32.029870] NVRM: drivers including, but not limited to, vesafb, may result in
[   32.029872] NVRM: corruption and stability problems, and is not supported.

```
This is in my blacklist-framebuffer.conf file
```
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
blacklist intelfb
blacklist kyrofb
blacklist lxfb
blacklist matroxfb_base
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist rivafb
blacklist s1d13xxxfb
blacklist savagefb
blacklist sisfb
blacklist sstfb
blacklist tdfxfb
blacklist tridentfb
#blacklist vesafb
blacklist vfb
blacklist viafb
blacklist vt8623fb
```Should I uncomment vesafb?

---

