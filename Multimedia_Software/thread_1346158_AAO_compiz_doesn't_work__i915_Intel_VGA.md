---
title: "AAO compiz doesn't work  i915 Intel VGA"
date: 2009-12-04
forum: Multimedia Software
---

### Post by biga805 on 2009-12-04
[FONT=monospace]I'm using an Acer Aspire One Karmic 9.1 and I'm having problems getting Compiz to run. I've searched these forums, Compiz's site, and Google, but haven't really found anything solid.

output from lspci -vvv 

[/FONT]> biga@biga-laptop:/usr/lib/xorg$ lspci -vvv | grep VGA
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
I've done some pretty extensive pokin' around into this, but still haven't found a solid solution.  I'm not trying to output to another monitor.  I had 9.04 until i decided to wipe the dualboot'd XP off my drive.  

Everything was working perfectly in 9.04, but I'm having problems loading Compiz.  I found some xorg.conf tweaks.. but.. surprise, no xorg.conf, what's up with that?

I've tried Fuzion-icon, compiz --replace, and other workarounds.  So the questions I have are:
Can I downgrade the Intel driver that was being used in 9.04 and 9.14 still work?

And, if not

What is the link for the Jaunty iso so I can wipe Karmic, and put it back on..

Thanks.

---

