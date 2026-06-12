---
title: "(TV) Video output is &quot;Blue&quot; with Xv/x11 output on SiS 650 onboard AGP"
date: 2005-11-28
forum: Multimedia &amp; Video
---

### Post by motionsiren on 2005-11-28
Intro: I'd like to use my TV card (WinTV PCI) on Ubuntu 5.10 using my onboard SiS 650 video chipset. I have used all the same hardware, except for a nVidia card, and everything worked out-of-the-box. So I suspect this is a Xv/x11 video output issude with my xorg.conf and friends.

Problem: when I open up tvtime, i get a blue screen. Not the normal blue, but more like the "Hi im the color blue that means you're getting no overlay support". All my conf's are OEM, just as they were with my nVidia card installed (and everything worked that time), so this must be a xorg + SiS chip issue.

Logs:
[lspci](http://bpk.deepdream.org/lspci.txt), [dmesg](http://bpk.deepdream.org/dmesg.log), [Xorg.0.log](http://bpk.deepdream.org/Xorg.0.log), [xvinfo](http://bpk.deepdream.org/xvinfo.txt), [xorg.conf](http://bpk.deepdream.org/xorg.conf)

Debugging / Testing: theirs a tool, "gstreamer-properties" which displays video in/output options and a "Test" button. Testing both SDL and XWindows (NO xv) displayed the generic color band test image and ACTIVE TV static in the lower righthand corner of the test image. Selecting Xwindows x11/XShm/Xv output reproduced the "Blue" screen.

Thank you for taking the time to look into this problem.

---

