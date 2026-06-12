---
title: "Need help with refresh rate settings (from shell) (newbie)"
date: 2005-10-15
forum: Multimedia &amp; Video
---

### Post by mike_esper on 2005-10-15
Here is my problem: (*now fixed, see replies below*)

It is an older computer with an older monitor.
I can run 5.04 Live-CD in expert mode by specifying 800x600 and 75 Hz refresh. (However, I just get a garbled screen--unusable--if I use the normal, non-expert boot up).

Therefore, Ubuntu **can** work on my hardware.

The problem comes when trying to install 5.10 "install version". (I never tried the 5.04 install version, would that make a difference?)
**The "expert" mode did not give me any refresh options, only for resolution**. Therefore it boots up to the **garbled screen** as before. I tried this twice so I didn't just accidentally miss it.
The non-expert mode gives the same garbled screen.

I can boot from GRUB into a recovery mode(? I think that's what it's called) which gives me a root shell terminal (sorry if that's the wrong terminology, it's something like root@ubuntu# ???)

I poked around in some old Google groups posts looking for a way to edit a config file to change the monitor settings (resolution and refresh rate) but they all didn't work (they were for Debian).

Is there a way to fix this **from the shell**? (I can't do anything within GNOME because the screen is garbled)

And if there is, could you post explicit instructions for a newbie? Or direct me to the appropriate website or forum post?

Thanks.

---

### Post by mlomker on 2005-10-15
> Is there a way to fix this **from the shell**? (I can't do anything within GNOME because the screen is garbled)

Have you tried **sudo dpkg-reconfigure xserver-xorg**?  You can select your driver and the screen resolutions that you want.

You could experiment with modelines using **sudo nano /etc/X11/xorg.conf**.  It'd be a lot easier to try another driver or resolution first (vesa is generic).

---

### Post by mike_esper on 2005-10-15
Using
"dpkg-reconfigure xserver-xorg"
from the shell as root and choosing "vesa" as the driver has fixed this problem. 

Using the "cirrus" driver (my card's chip) didn't let me get above 640x480 but since the "vesa" works at 800x600 (my desired resolution) that is fine with me. This is an old video card so I'm not going to be playing games or anything.

Thank you for your help.

---

