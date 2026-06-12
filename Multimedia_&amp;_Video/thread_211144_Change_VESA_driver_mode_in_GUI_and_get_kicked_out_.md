---
title: "Change VESA driver mode in GUI and get kicked out to desktop manager screen!?!?"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by sigmason on 2006-07-07
Okay perhaps nobody caught this, but I've got a real simple bug.

If you get into Gnome, KDE or Xfce with the VESA driver and then change your video mode (from say 1024x768 to 800x600) you'll get a black screen, then get kicked straight out to the desktop manager either GDM or KDM.  If you log back in, your settings did not stick, your mode is still the same.

I've now verified this on 8 computers by booting into "Safe Mode" on the Ubuntu 6.06LTS ISO and trying it and I have Ubuntu Desktop on my Dell Latitude C800 w/ATI Rage Mobility M4 and it does the same thing (I even reinstalled the gnome utility and randr before I decided to test the CD elsewhere.)

It applies to NVidia, ATI, S3 and Trident.

So here's the question, why does it only apply to the VESA driver, the changes work fine in the Xorg ati, nvidia, etc drivers.  When, if you use dpkg-reconfigure xserver-xorg or edit xorg.confg manually, it boots into those modes just fine.

Something seems off about this, also, if you do this sometimes you loose your ability to switch to consoles with CTRL-ALT-Fx the screen simply gets locked black no choice but to reboot.

Anyone else confirm this behavior?

sigmason

---

### Post by sigmason on 2006-07-07
Oh joy, I just downloaded a Mandrake 9.2 based LiveCD distro: pclinuxos

Guess what, use the VESA driver, change modes using KDE and BOOM.
Fatal server error: Caught signal 11.

Same as (k/x)ubuntu, guess this one isn't a (k/x)ubuntu issue or a debian issue either.  [-( 

It also had the same issue on the other systems and cards so this is a bug, though, LOL, at least in pclinuxos Configurator, they tell you change the driver (it changes xorg.conf), log out, and then hit CTRL-ALT-BACKSPACE and log back in.  Quite smart, they must know so they circumvented it.

sigmason

---

