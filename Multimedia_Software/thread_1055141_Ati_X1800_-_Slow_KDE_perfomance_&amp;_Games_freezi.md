---
title: "Ati X1800 - Slow KDE perfomance &amp; Games freezing"
date: 2009-01-30
forum: Multimedia Software
---

### Post by enosis on 2009-01-30
Hi all,

Me and my wife recently made the switch to Linux (I've tried various distros over the past years). Although kubuntu runs fine at my computer (I have nvidia card), in my wife's computer it does not perform very well.

She has an Ati X1800. Initially I installed the proprietary ati driver that kubuntu suggested (from a popup window). As the performance in KDE (4.2) was not so great, I download and installed the driver 9.1 (I selected the option to install the generic version, not distro-specific).

Now, some problems that I have are:

1) Some sluggish performance at KDE (even after disabling the composite effects).
2) Sometimes when I play a video, or an mp3 with visualization effects from the player, the screen goes black for a second every few seconds.
3) I tried to check the 3D performance, so I installed the game Alien Arena and launched it. I got to the menus, started a game, and as soon as the game started and I saw the first 3D graphics, the computer froze there and I had to reboot. 

From the catalyst control center, I have set everything for performance. Catalyst A.I. is set to "advanced" and vsync is "always on".

One question that I have, is should I had first remove the proprietary drivers installed by kubuntu before installing 9.1? Should I try re-installing them with the "distro-specific" version? If yes, should I first uninstall everything and start over? 

In general, do you have any idea why these problems happen (besides ati's bad drivers :P )?

Also, just to mention that before kubuntu, she was running Vista with aero enabled and it was running smoothly. Also she was running games like world of warcraft with very good performance, so it's not that the pc can't handle the load.

The computer is an Athlon X2 4400, 2gb ram, Ati X1800 XT 512.

Thanks in advance

---

### Post by ultrageeky on 2009-05-18
I've an ATI Radeon 3600 and Kubuntu 9.04 is extremely slow.  As you said, the screen often turns black for a second or two then returns to normal.

To explain how sluggish it is, the boot sequence (from switching on to getting a loaded desktop) takes up to 10 minutes - the longest wait starts with the splash screen with the icons showing the hardware being set-up.  When I click the Kmenu there's a 30 second delay for it to open then it takes 10 seconds to access submenues.  Programs take upwards of a minute to load.  Once a program/menu has loaded once it loads quicker the second time.

At first I thought the problem was due to something I'd installed post set-up so I re-installed the OS; I've tried EnvyNG (QT) but that only made the system unbootable and unfixable.  I tried reconfiguring all packages in the first installation and there was a slight improvement until I restarted the system.

The Live CD works as fine as can be - if I could run the system through the live CD and splice my user settings from a HDD partition I'd be happy with the performance but the way it works when installed is, frankly, pathetic.  I'd downgrade to 8.10 but I understand it has a short (and limited) support life.

I'd suspect my HDD to be the cause of the sluggishness except that I've now tried it on two HDD's and non-graphical programs (ImageMagick etc) are as responsive as they should be.

If anyone has a solution then please post it.

---

