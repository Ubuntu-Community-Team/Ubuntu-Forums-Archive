---
title: "video sync fixed and flash video fixed"
date: 2010-04-29
forum: Multimedia Software
---

### Post by Cresho on 2010-04-29
a.  install drivers from hardware drivers
b.  sudo gedit /etc/X11/Xsession
c.  add "nvidia-settings -l" right above "set -e"  without quotes. then reboot
d.  "nvidia-settings" enable vsync on video and in opengl. 
e.  install "sudo apt-get install compizconfig-settings-manager"
First off, in the application under system->preferences->compizconfig settings manager->General settings->Display settings
Change the texture filter to "best", untick"detect refresh rate"(this one was the one that made a difference and reboot the system between changes), bump to 200 "refresh rate", tick "Sync to vblank"

I'm assuming your compiz is already loaded at boot.
now your flying!

sorry for being so vague.

---

