---
title: "[SOLVED] Video Drivers Broke- Can't boot"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by ace214 on 2007-10-08
I'm running Ubuntu Studio Gutsy with a Radeon x300 and a VGA monitor.


I had things running ok. I think I installed the official ATI driver way back but I don't think it ever worked properly cus i would get these XFree86 warnings when booting up like winefile and stuff like that and recently, with the new little appearance settings, compiz says it can't boot desktop effects. So I went and  followed [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") and used the restricted driver thingy to install a new driver. I didn't try to uninstall the other one first... Next time I boot up Ubuntu, when it should be at the loading progress bar splash my monitor says "Frequency too high. Set a lower resolution or see the manual." So yeah... I can get into the recovery and stuff. I'm hoping I can go in with Knoppix or windows and edit some configuration file??? If not, I guess I'll have to reinstall??

Thanks for any help...

SOLVED:
Uninstalled ATI drivers
Manually edited the monitor H and Vs in xorg.conf

---

