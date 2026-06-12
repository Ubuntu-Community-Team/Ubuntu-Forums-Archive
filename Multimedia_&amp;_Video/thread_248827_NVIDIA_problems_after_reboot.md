---
title: "NVIDIA problems after reboot"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by dummkauf on 2006-09-01
I have recently switched to Ubuntu from gentoo and thought I had my xorg configuration figured out for my dual-head system.  After installing Ubuntu I installed the Ubuntu nvidia drivers and configuration applications, I then copied my old xorg.conf file from my previous gentoo system into /etx/X11/  Then I started my X server and everything loaded up perfectly, my dual-head system worked just like it had before, no problems.

The problem now is that after working that one time, I have not been able to get it working since I rebooted it.  Every time I try and start the X server it fails to load and gives me an error message about being unable to find the  nvidia module.  I then issued a 'modprobe nvidia' command which loaded the nvidia module, but even after that X still will not load and continues to give me an error about not being able to find the nvidia module.

If anyone has any suggestions on this your help would be greatly appreciated.  Also let me know if you would like my xorg.conf file posted, or any log files.

---

