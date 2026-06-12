---
title: "HP Pavilion dv7 media hotkeys not working."
date: 2013-05-04
forum: Multimedia Software
---

### Post by DarkSwordmaster on 2013-05-04
Hi to anyone who reads this.

Well, my problem basically is the stated above. My media hotkeys, including volume, mute, play/pause, etc, aren't working with Xubuntu 12.04.
I have a HP Pavilion dv7 laptop and have tried a lot of distros in it and my media hotkeys have worked, except with Xubuntu this time. Right now i can only control sound with my mouse or change songs by clicking the buttons and that's not practical at all when running full-screen applications.
Volume and mute keys are the ones I would like to use mostly. When I press them, a volume pop up appears showing that I am changing the volume or muting it but when you check the volume adjustments, they haven't changed at all. I tried changing the active card settings on the xfce4-mixer, setting shortcut commands to each key, and neither of them worked.
As I wrote before, this only have happened to me with Xubuntu.

Thanks to anyone who tries to help.

---

### Post by dentaku65 on 2013-05-05
Choose Setting Manager -> Session and Startup and enable GNOME Settings Daemon; reboot.

---

### Post by DarkSwordmaster on 2013-05-06
Thanks, didn't know that XFCE was having problems with media keys ultimately.
I had to download gnome-settings-daemon first, then disabled xfce4-volume, enable gnome daemon and rebooted. Everything is working now.

---

