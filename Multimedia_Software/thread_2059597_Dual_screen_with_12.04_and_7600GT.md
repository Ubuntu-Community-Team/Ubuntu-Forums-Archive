---
title: "Dual screen with 12.04 and 7600GT"
date: 2012-09-18
forum: Multimedia Software
---

### Post by the music man on 2012-09-18
I'm trying to setup my two monitors to work with my GeForce 7600GT card and Ubuntu 12.04.

Here's my progress so far:
[LIST=1]
[*]Enabled the v173 driver
[*]Rebooted and got desktop effects, so it works
[*]sudo nvidia-xconfig for a clean xorg.conf
[*]Reboot, everything still working on one screen
[/LIST]

When I run sudo nvidia-settings, I see the following configuration:
[ATTACH]224316[/ATTACH]

Is it right that the two screens are disabled? Anyway, in an attempt to get a dual screen configuration, I try to set them both to 'Separate X screen'. Then I save the configuration and reboot.

After the reboot, all desktop effects are gone, and all I got is everything duplicated on the second screen. I also get a compiz crash message. Sometimes even my network connectivity is gone.

When running sudo nvidia-settings, I get an (apparently known) error message: 'You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.'

When I remove the 173 driver, I can reproduce all this from step 1.

What am I doing wrong?

---

### Post by oldfred on 2012-09-18
Please attach screenshots with the paperclip icon in the edit panel above the message. 

Why are you using the 173 driver. I have a 9600GT and the nVidia driver I have is 304.43? nVidia is changing around which drivers support which cards. But yours should still be the current driver.

GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

This all should be older info:
NVIDIA 295.49 Fixes Linux Performance Regression
[http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ)
Fixing the performance regression of the 295.40 driver that affected GeForce 6 and GeForce 7 series hardware. 

Warning for nVidia GeForce 6, 7, and 8800 cards with 12.04 Precise
[http://ubuntuforums.org/showthread.php?t=1969754](http://ubuntuforums.org/showthread.php?t=1969754)
serious issue with the GeForce 6, 7, and 8800 GTS/GTX cards, K/Ubuntu 12.04, and their latest 295.40 driver.

---

### Post by the music man on 2012-09-18
I installed the 304.43 driver now, because of the issues described in the second article you provided. After installation TwinView was enabled automatically, and now I can adjust my monitor settings with the built-in Ubuntu configuration.

Thanks for the information!

---

### Post by QwUo173Hy on 2012-10-27
> **the music man said:**
> I installed the 304.43 driver now, because of the issues described in the second article you provided. After installation TwinView was enabled automatically, and now I can adjust my monitor settings with the built-in Ubuntu configuration.

Thanks for the information!
I have the same graphics card. Does 304.43 give any other improvements over 173 beside dual screens? I'm finding Unity sluggish and games often exit badly leaving the desktop locked up.

---

