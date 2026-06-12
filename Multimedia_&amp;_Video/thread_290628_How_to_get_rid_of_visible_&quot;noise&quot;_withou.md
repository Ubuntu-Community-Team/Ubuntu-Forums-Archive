---
title: "How to get rid of visible &quot;noise&quot; without limiting resolution to VESA?"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by xp_newbie on 2006-11-01
My system with an ASUS V9400 video card (also identified as NV18 [GeForce4 MX 4000 AGP 8X]) generates some "visual noise" whenever I move the mouse or type on the keyboard - under Ubuntu 6.0.6 (Dapper).

This same exact system doesn't exhibit this problem when running Windows 2000 (dual boot). Thus, I know that this is not a hardware problem but rather something in the software (Linux drivers? Ubuntu desktop?).

A while ago I had a similar problem in a **different system** (Matrox MGA200 based), but the only advice I received was to configure my xorg.conf file to VESA - which limits resolution to 1024x768. I am used to work in 1600x1200, so obviously this solution is not acceptable for me.

Is there a way (or "trick") to get rid of this "visual noise" while using the optimized drivers used for my display adapter? Surely if Windows 2000 can do that, Linux can do that too, right?

If so, how to I accomplish that?

Thanks!
Alex

---

### Post by tseliot on 2006-11-01
Try Method 1 of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by xp_newbie on 2006-11-01
Thanks! I am trying now to follow your excellent guide, but I stumble on something which I am not sure that I understand:

I did uname -r and received: **2.6.15-27-686**

So I typed "**sudo apt-get install linux-686**" and the dpkg log file reports:

> 2006-11-01 14:43:34 install linux-686 <none> 2.6.15.25
2006-11-01 14:43:34 status half-installed linux-686 2.6.15.25
2006-11-01 14:43:34 status unpacked linux-686 2.6.15.25
2006-11-01 14:43:34 status unpacked linux-686 2.6.15.25
2006-11-01 14:43:34 status unpacked linux-686 2.6.15.25
2006-11-01 14:43:34 status half-configured linux-686 2.6.15.25
2006-11-01 14:43:34 status installed linux-686 2.6.15.25


But I have a newer version of the kernel installed (2.6.15-27) and when I type again 'uname -r' I still get 2.6.15-27-686. I hope I didn't break something in the system...

Anyway, I proceeded with the rest of the instructions (installed nvidia-glx and typed nvidia-xconfig) and now everything works perfectly!

Thanks you so much!

Alex

---

