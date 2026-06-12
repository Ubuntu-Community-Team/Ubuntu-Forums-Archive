---
title: "Help! Deep into nVidia screen resolution doo-doo"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by earther on 2007-07-29
I finally got Ubuntu up and running on Friday.  It dual boots with XP on a new 250GB drive.  The USR internal serial modem worked right out of the box.  Things were sailing along smoothly until I wanted to change the screen resolution.

There was no option to change it to 1152 x 864 in Preferences  - the highest available was 1024 x 768.  I was guided through resetting the options via terminal (and a BIOS-like gui) but the changes wouldn't stick.  So the techie helping me burned an nVidia driver to a cd (along with some dialup unfriendly stuff for installation) and gave me these commands to run:

> cd /media/cdrom/debs
sudo dpkg -i ./nvidia-glx*
sudo dpkg-reconfigure -phigh xserver-xorg

After doing that, I got to the gui again, ticked the resolution I wanted available and rebooted.  Uh oh . . . deep doo-doo.   The screen is now displaying some weird vertically stretched resolution that cuts off the taskbar so I can't get to anything.  I tried resetting the screen and raising the display vertically but no joy.  No resolution is indicated on the Samsung monitor adjustment menu - it usually shows refresh rates, resolution etc. (but I can't change it from there).

How can I fix this??!   My techie won't be available till tomorrow and I want Ubuntu back!!!

---

