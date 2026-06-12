---
title: "Is there a gui app for selecting xorg driver?"
date: 2009-05-23
forum: Multimedia Software
---

### Post by deruberhanyok on 2009-05-23
I have a Radeon 4850 in my system right now. My display is a Toshiba 32RV530U LCD TV. I was using whatever driver was installed by default with 9.04. The "display propeties" GUI applet detected my TV properly, allowed me to select the various supported resolutions and refresh rates and I had no problems.

I tried to use the proprietary drivers in the repository (Catalyst version 9.4) and ran into some problems - refresh rate locked at 24hz causing whole system to seem choppy, CCCLE doesn't seem to actually do anything when I change the settings, can't open the display properties dialog to try changing it there - so I uninstalled it. 

Today I ran envy-ng thinking it might install 9.5 but its behavior seems to have changed from when last I used envy. It installed 9.4 and I had the same problems. So I removed it (with envy-ng) and now I seem to be using the some kind of default display driver. The "display properties" applet isn't detecting anything properly and I'd like to switch it back to, idunno, ati or radeon or radeonhd, whatever open source one it was using.

I swear there used to be a way to select the open source driver from a list but I can't find it anywhere. I'll actually reinstall Jaunty before having to manually edit an xorg.conf file, so, is there still a gui applet to change the driver or should I just forget it and reinstall?

---

### Post by sb73542 on 2009-05-24
No, there is no GUI for xorg.conf.  The users have begged for a GUI for years, and have been consistently ignored.

---

### Post by x33a on 2009-05-24
maybe you can find the driver through synaptic.

 system->administration->synaptic package manager

---

### Post by Arup on 2009-05-24
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

Go there and add their repo and you will get the latest stable tested release from Canonical for your ATI.

---

### Post by deruberhanyok on 2009-05-24
Thanks for the info all. Finding the drivers hasn't been a problem, I just figured there'd be a way to select which driver to use without editing a config file. With so much able to be done without text editing these days, the xorg.conf thing just seems anachronism to me.

---

### Post by Melcar on 2009-05-24
Doesn't KDE have a GUI of sorts for driver selection?  KDE3 did at least.

---

### Post by pbpersson on 2009-05-24
> **sb73542 said:**
> No, there is no GUI for xorg.conf.  The users have begged for a GUI for years, and have been consistently ignored.

Mint is always mentioned as a friendlier version of Ubuntu.  I am curious, do they have a GUI for this?

---

### Post by Melcar on 2009-05-24
I heard that xorg.conf is being removed eventually, so if that's true I doubt anyone will bother making a GUI.  KDE3 had a xorg driver selection GUI of sorts (thought it never worked for me), but that seems to have been removed in KDE4.  I doubt GNOME will ever have one, due to the "keep it simple stupid" philosophy.

---

### Post by pme 72 on 2009-05-25
My Hardy partition has a program called "Screens and Graphics" under Applications/Other. I may have added it by right clicking on Applications and choosing Edit Menus. 

Last week I was trying to enable the Radeonhd driver which is listed in that program but I was not successful. I managed to completely lose my desktop. I had to reboot and choose Recovery Mode from the boot menu to regain my desktop. Maybe that is why they do not install it by default. If you find a "How To" for Screens and Graphics" let me know...

---

