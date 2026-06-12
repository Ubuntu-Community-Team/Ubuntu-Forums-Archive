---
title: "Black screen of death - can't start x"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by DarrenO on 2007-09-30
I am a Feisty Ubuntu user and a while ago I changed from fglrx to ati drivers with no problems (Intel 3 GHz box, LG widescreen LCD with an ATI Radeon 9600 card). Followed this guide:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

The ati driver seemed much better - everything worked a treat. Then one day, I got the black screen of death instead of a login window for Gnome. No key combos would bring me out of the black screen and back to the console. Instead I rebooted to console and ran dpkg-reconfigure. I am able to get VESA working with no problem and if I reinstall fglrx, it will work fine but for the life of me, I can't get the ati driver to work again. It makes no difference if I am starting xserver from console or from a clean boot, it gets hung up at the same point - just when you would expect the login screen to pop up.

I did not black list fglrx (don't know how to) - could that be the cause of my problems? I did uninstall the fglrx drivers, but perhaps there is some remnant conflicting.

Looking for some things to try. Any help appreciated.

Attached is my xorg.conf and Xorg.0.log files. I don't know what I am looking for in the log file or if this is of help at all.

Darren

---

