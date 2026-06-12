---
title: "Screen resolution gets reset at every reboot (Jaunty)"
date: 2009-07-30
forum: Multimedia Software
---

### Post by Ctulhu on 2009-07-30
I am using Ubuntu 9.04 on a Dell Latitude E6500 with a NVIDIA Quadro NVS 160M. After some problems with getting an external data projector to be recognized, my display resolution (max possible: 1900*1200) always got reset to 1024*768. To fix that and the data projector issue, I un and then re-installed all Nvidia drivers and setting from my machine. However, the coarse resolution problem persists: the system starts up and gives me 1024*768, and I have to change this in nvidia-settings manually even when I start nvidia-settings with sudo, set it to 1900*1200, and have the gui save the result into the xorg file - any hints?
Thx,
C

---

### Post by xc3RnbFO8P on 2009-07-30
Check System> Preferences> Display> choose **NO**, and see if you can change the resolution there.

---

### Post by Ctulhu on 2009-07-30
Geez, how grateful am I to you ... :-))) Thx, man, I was close to re-installing the OS.

---

### Post by prince_niceguy on 2009-08-26
> **Ringi said:**
> Check System> Preferences> Display> choose **NO**, and see if you can change the resolution there.

thank you saved my life... every time i booted the screen resolution use to become 1080p and i was not able to read the same from a distance... now it is all set to 1366 x 766...

thank you....

---

### Post by peepingtom on 2009-08-26
When you have time you might want to try the latest nvidia driver (185, 190 is beta) from this PPA [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

Make sure to uninstall all old drivers except nv and install the nvidia-settings package that corresponds to your driver. When you save in nvidia-settings (run as root) don't merge x.org files, rewrite the old one.

I assume you're running open source nvidia drivers now? I bet you can fix the settings with the proprietary ones, I think your card can decode video with VDPAU and it's totally worth it to put some effort into it. I'll be back to check on y'all!

edit: 3 weeks old?!?! Well i'll still be back :p

---

### Post by prince_niceguy on 2009-08-26
> **peepingtom said:**
> When you have time you might want to try the latest nvidia driver (185, 190 is beta) from this PPA [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

Make sure to uninstall all old drivers except nv and install the nvidia-settings package that corresponds to your driver. When you save in nvidia-settings (run as root) don't merge x.org files, rewrite the old one.

I assume you're running open source nvidia drivers now? I bet you can fix the settings with the proprietary ones, I think your card can decode video with VDPAU and it's totally worth it to put some effort into it. I'll be back to check on y'all!

edit: 3 weeks old?!?! Well i'll still be back :p

Sorry I cannot test this, I am having hd3200 ati. else would have given a shot at the ppa.

---

### Post by blackest_knight on 2009-09-01
> **Ringi said:**
> Check System> Preferences> Display> choose **NO**, and see if you can change the resolution there.

Thanks very much for this useful post i'm using the nvidia  185 driver and i kept getting put into 640x480 mode although nvidia-settings would allow me to choose the correct resolution until the next reboot using the native screen resolution tool solved the problem thank you. 

this worked very well on ubuntu karmic alpha

---

### Post by shields on 2009-11-07
> **Ringi said:**
> Check System> Preferences> Display> choose **NO**, and see if you can change the resolution there.

That worked!

Thanks! :D

---

### Post by KuifjePDX on 2009-11-07
I'm using Karmic Koala (Edubuntu 9.10) with the recommended nvidia driver (185) and every time I log in as administrator the screen resolution is reset to 800x600 64Hz and the display pops up a message stating that 1440x900 60Hz is the recommended setting.

I use sudo nvidia-settings to change it and save it to the Xconfiguration file. No errors are shown and the xorg.conf file shows the correct display settings when I check them in gedit.

There are three user accounts on this computer as well and all three log on with the correct display settings (1440x900 60Hz). Only the administrator account is reset EVERY SINGLE TIME!

So what am I doing wrong, and what should I be doing to keep the high-res screen resolution when I log on as Administrator.

Keep in mind that the opening (splash) screens for Ubuntu ARE shown in the high-res setting. The display settings change AFTER I enter the administrator password and hit enter.

I tried the proposed solution of going System->Preferences->Display->No. The window there shows the correct display setting of 1440x900 but only the refresh rate offered is 50Hz.

UPDATE: I just tried the above solution again when the screen resolution is low. This time it DOES work. When this solution is tried after you increased the screen resolution with the Nvidia control panel its settings are not retained. So far so good.

---

