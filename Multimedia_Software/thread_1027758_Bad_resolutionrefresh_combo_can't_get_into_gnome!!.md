---
title: "Bad resolution/refresh combo can't get into gnome?!?!"
date: 2009-01-01
forum: Multimedia Software
---

### Post by tricky37 on 2009-01-01
Just posted this in wrong category but this is likely it's proper home...

I recently installed drivers for an ATI Radeon 9000 in Ubuntu 8.10...
I believe it was my first restart after that and i got an error and had to boot in low graphics mode. That set me in 1280X1024 when i got in, i went to res settings and dropped to 1024X768 and that scrambled the screen. Now i can't get anything past login screen, once i log in it changes resolution and scrambles screen. i have changed, deleted etc etc to xorg.conf and tried the dpkg reconfigure....

I have exactly the same problem as this post:
[http://ubuntuforums.org/showthread.php?p=5619324](http://ubuntuforums.org/showthread.php?p=5619324)

however I don't seem to have the same monitor settings file....

any advice would be VERY appreciated

I am desperate....

---

### Post by pietjanjaap on 2009-01-01
Install envy, is inside of ubuntu.
Go to the envy website(google), there you can find the textmode instructions.
To start envy in textmode sudo envyng -t, then you get a menu in textmode.
Choose remove drivers, (the ubuntu will start again without drivers if you want).
Now reboot to recovery mode,
choose x fix (here your video card and monitor will be search.
then go to textmode,
install your driver with sudo envyng -t
reboot.
If your screen size is not ok, go to system-preferences-screen resolution, and change it, and reboot.

If you install the video driver with envy with gui, then you can choose 3 drivers(nvidia), you have a old card so choose the oldest.
If it goes wrong always remove everything and start from the beginning.


So if you get in problems, you can always remove your drivers, boot in ubuntu and work with grafics screens.

---

