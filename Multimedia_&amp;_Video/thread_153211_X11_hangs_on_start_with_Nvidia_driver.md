---
title: "X11 hangs on start with Nvidia driver"
date: 2006-03-31
forum: Multimedia &amp; Video
---

### Post by nouse66 on 2006-03-31
I have a GeForce FX 5200 card and can't get the Nvidia driver v. 1.0.7667 that I install via automatix to work.  Once X starts I get either a blank screen or the Nvidia logo screen (depending on the option I choose is xorg.conf) and the system seems to hang. There is no reponse to the keyboard and I just end up having to reboot with the power button. If I use the standard nv driver I have no problems.

I saw this behavior before when I was running Gentoo but was able to fix it by switching to version .7667 of the driver.... the exact version I'm using in Ubuntu. Does anyone have any ideas on what could be causing this?  I know I could download the newer version and see if that works but I'd rather stick to the default package if possible.

Thanks!

Also: no errors show up in the x.org logs

---

### Post by nouse66 on 2006-04-01
I figured out that setting: Option "NvAGP" "0"
gets it working.

---

### Post by nouse66 on 2006-04-01
oops

---

