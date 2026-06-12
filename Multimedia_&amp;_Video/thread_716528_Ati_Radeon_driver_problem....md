---
title: "Ati Radeon driver problem..."
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by lentzu on 2008-03-06
I have an Ati Radeon X1550 series and I can't find a driver for this in Ubuntu 7.lalala OS...Need directions...

---

### Post by Kivech on 2008-03-06
Well, you basically have two options:

1) Install the latest ATI driver manually. (quite  a complicated job and I myself didn't have success with it on my ATI Radeon x1900 card, it's also buggy still).

2) Go with the default proprietary driver that comes with Ubuntu and settle with the possibility that you won't have direct rendering (usually only needed for certain games or if you are a developer that makes 3d applications).

For option 1 I would refer you to the sticky on top of this forum. It says something like: Howto install the properietary driver on any stable Ubuntu version.

For option 2 you just follow these steps:

1) Make sure all software is updated. In the menu System>Administration>Update Manager and have it check for updates. If there are any apply them.

2) Install the ATI proprietary driver: System>Administration>Restricted Drivers Manager.
Check the checkmark next to the driver to install it, reboot and you are set for the driver.

3) To get compiz going (the special desktop effects) what I had to do was install both xserver-xgl and compizconfig-settings-manager. You can find those in the package manager System>Administration>Synaptic Package Manager. Do a search for both and mark them for installation. 

4) Reboot and set desktop effects in System>Preferences>Appearance. On the last tab you can enable the special effects.

And you are set. However there are lots of people not getting direct rendering enabled this way. Hence the reason why a lot refer to option 1.
I personally tried it, but for me it didn't work properly. I couldn't play any type of video anymore. Since I don't play any games that require direct rendering, I reverted back to the second option. It's also much easier to install.

If you want to try both, I would first go with option 2 and then try option 1. The paradox being that going back to the second option isn't as easy as it seems and forced me to do a reinstall of my system, so the whole thing is not without risk.

As always, make sure you make a **good backup** of your whole system when you start playing with video stuff. So in case you mess it all up, all you have to do is reinstall and put your backup back. Fortunately in Ubuntu that isn't too much work.

Good luck!

Kivech

---

### Post by markoloka on 2008-03-06
In this section...look for those Stickys.

---

