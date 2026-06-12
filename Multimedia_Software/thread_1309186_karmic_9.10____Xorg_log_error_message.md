---
title: "karmic 9.10    Xorg log error message"
date: 2009-11-01
forum: Multimedia Software
---

### Post by robin0800 on 2009-11-01
"XAA Render acceleration unsupported on Radeon 9500/9700 and newer. Please use EXA instead."

If I enable EXA, as this log suggests, 2d performance is simply appalling and takes ages to render. Searching suggests its either the community driver, the Xorg server, or the new kernel
This used to work until recently. Any help, guidance or bug reports welcome.

---

### Post by Yellow Pasque on 2009-11-01
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/363238](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/363238)

---

### Post by robin0800 on 2009-11-01
> **Temüjin said:**
> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/363238](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/363238)

Yes your right all I had to do was add

 **Option     "FBTexPercent"       	"0"**

in the xorg.conf file to get EAX working again

---

