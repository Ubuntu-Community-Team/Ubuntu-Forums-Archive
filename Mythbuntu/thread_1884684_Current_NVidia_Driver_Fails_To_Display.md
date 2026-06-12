---
title: "Current NVidia Driver Fails To Display"
date: 2011-11-21
forum: Mythbuntu
---

### Post by jamoody on 2011-11-21
I've recently switch to Mythbuntu 11.04 with up to the day fixes with GeForce 9500 GT graphics card and VDPAU isn't working.  /proc/driver/nvidia/version shows I'm running driver 173.14.30.  I tried to use Mythbuntu Control Centre to change to "current" driver, but on reboot the driver wouldn't initialize leaving the screen in text mode and useless.  Fortunately I could VNC in and use Mythbuntu Control Centre to change it back.

VDPAU used to work with the same hardware running MythDora 12.24-6 using driver 195.36.31.

Any ideas 1) if failing VDPAU is a driver issue, 2) why I can't use current NVidia driver with  Mythbuntu Control Centre?

Thanks.

---

### Post by jamoody on 2011-11-30
Anybody have any ideas on this?

---

### Post by nickrout on 2011-12-01
yes, read /var/log/Xorg.0.log

---

