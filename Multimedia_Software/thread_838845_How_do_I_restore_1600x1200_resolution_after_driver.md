---
title: "How do I restore 1600x1200 resolution after driver upgrade?"
date: 2008-06-23
forum: Multimedia Software
---

### Post by xp_newbie on 2008-06-23
Installed Ubuntu 8.04. Right out of the box it gave me the screen resolution that I wanted: 1600x1200.

But "out of the box" was using generic Ubuntu drivers for my ASUS EN8600GT SILENT/HTDP/256M graphics card (nVidia GeForce 8600 series). It created lockup/freeze problems which seems to have been solved by enabling "NVIDIA accelerated graphics driver" (AKA restricted/proprietary). That also enabled compiz (nice! very nice!)

That is great, but the maximum resolution I can now set via System > Preferences is 1280x1024.

How do I re-enable the 1600x1200 resolution?

Thanks,
Alex

---

### Post by anindya_m on 2008-06-24
Try running the nvidia-settings tool and change resolution from there.

---

### Post by xp_newbie on 2008-06-24
> **anindya_m said:**
> Try running the nvidia-settings tool and change resolution from there.
Thank you for your answer. I looked for an executable named 'nvidia-settings' but couldn't find any on my system. The only ones (with 'nvidia' in them) that I could find were:
```
/usr/bin/nvidia-bug-report.sh
/usr/bin/nvidia-xconfig
```
Where do I find the nvidia-settings tool?

Thanks,
Alex

---

### Post by Pjotr123 on 2008-06-24
Read this simple how-to:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

---

### Post by xp_newbie on 2008-06-24
> **Pjotr123 said:**
> Read this simple how-to:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )
Thank you! The first step (**gksudo displayconfig-gtk**) got me my 1600x1200 back.:)

But the refresh frequency is at 57Hz max (when it should be 85Hz, just as in my Ubuntu 6.06).

So I downloaded 'nvidia-settings' (using package manager) and ran it. Wow! it gave me my 1600x1200 @ 85Hz back.

But Ubuntu's System > Preferences now shows 103Hz. Strange.

---

### Post by anindya_m on 2008-06-24
The Ubuntu default tools sometimes report wrong values for the nvidia cards. I have seen this before. The best option is to always use nvidia's utility and bypass Ubuntu's generic tools in this case.

---

