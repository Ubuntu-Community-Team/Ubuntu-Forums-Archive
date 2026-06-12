---
title: "Can't get 1280x1024: insufficient memory"
date: 2005-12-31
forum: Multimedia &amp; Video
---

### Post by gauss on 2005-12-31
I have a Dell UltraScan P780 17" monitor. The specs say that it supports 1280x1024 as a VESA mode but I can only get 1024x768 under Breezy. The video card's chip is Riva 128. I've tried putting in an extra modeline for 1280x1024 but this didn't work.  My xorg.conf includes the correct HorizSync and VertRefresh. The X server chooses the nv driver (correctly, I think) for this video card. I also unsuccessfully tried the vesa driver instead of nv.

Here are parts of Xorg.0.log which show some problems:
```
(II) RIVA128(0): Supported VESA Video Modes:
...
(II) RIVA128(0): 1280x1024@75Hz
...
(II) RIVA128(0): Not using default mode "1280x1024" (insufficient memory for mode)
(WW) (640x512,DELL P780) mode clock 54MHz exceeds DDC maximum 0MHz
...
(II) RIVA128(0): Not using mode "1280x1024" (no mode of this name)
...

```
I'm fairly certain that both the P780 monitor *and* the Riva 128 chip (4 Mb memory) are capable of 1280x1024 since I could get this resolution with the same chip and a similar monitor under RedHat 9.

Any ideas on how to coax xorg.conf into doing "the right thing?"

Edit: Jason_25, below, solved my problem.

---

### Post by Jason_25 on 2005-12-31
Have you tried using 16-bit color depth in the xorg file instead of 24?

---

### Post by gauss on 2005-12-31
[QUOTE=Jason_25]Have you tried using 16-bit color depth in the xorg file instead of 24?[/QUOTE]
This works.

Strangely, the nv driver doesn't support 16-bit color but rather something (in the xorg.conf file) labeled "15-bit." But I'm delighted with the tradeoff of color bits for resolution.

Thanks!

---

