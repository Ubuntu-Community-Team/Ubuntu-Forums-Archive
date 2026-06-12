---
title: "DVD problems in Hardy"
date: 2008-05-25
forum: Multimedia Software
---

### Post by AndrewWalker on 2008-05-25
My DVD drive is driving me mad after an upgrade to Hardy. An icon appears for a DVD inserted but I can't play it. Xine reports it can't find an input plugin for dvd:/ which isn't surprising as Hardy has deleted /dev/dvd and called my DVD R/W /dev/scdo and /dev/dvd /dev/dvdrw /dev/cdrom have all been deleted. For some reason I now have a /dev/cdrom1 linking to /dev/scdo. This is but the tip of the iceberg though as I use this machine with mythtv. Mythvideo won't allow me to play the DVD either, but after trying to play it,mythfrontend crashes and I can no longer get the disk out!  The message I get is
Device to unmount is not in /media/.hal-mtab so is not mounted by HAL.
Does anyone have any ideas? I tried creating a soft-link /dev/dvd pointing to scd0 but it still didn't work.

---

### Post by mc4man on 2008-05-25
Atm kubuntu is somewhat broken as far as using cd/dvd drives, particularly if you have 2. Your best bet is to set your apps. individually to access a device ie. /dev/scd0, scd1. You'll get better functionality from vlc than you will with kaffeine.
you can read here [http://ubuntuforums.org/showthread.php?t=802980&page=2](http://ubuntuforums.org/showthread.php?t=802980&page=2)
and here for info on relationship between persistent rules and your links in /dev. [http://ubuntuforums.org/showthread.php?t=801771](http://ubuntuforums.org/showthread.php?t=801771)
Basically while /dev/various links directs the 'traffic' any changes you make there that conflict with what's in rules will be overwritten when you reboot.(fstab is a factor too, more so with 1 dvd drive)
If audio and video are very important to you than gutsy is far superior to either hardy release, as far as 8.04 I'd go ubuntu over kubuntu atm

---

