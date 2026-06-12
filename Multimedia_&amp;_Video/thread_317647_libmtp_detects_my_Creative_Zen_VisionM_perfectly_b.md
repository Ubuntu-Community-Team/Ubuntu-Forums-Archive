---
title: "libmtp detects my Creative Zen Vision:M perfectly but not gnomad2"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by LantagoniE on 2006-12-12
Hello there.

   This is my first post on the english board of Ubuntu.  For two days, i've been trying to gain access to my Creative Zen Vision:M through libmtp and Gnomad2 in my Ubuntu 6.10 and i've been having nothing but trouble at home whereas at work, i had it working like a charm within 5 minutes.

   I first downloaded, compiled and installed the sources of libmtp without problems and when i was going into the **/examples/** subdirectory of where my libmtp sources were, i could execute **./detect** and my Vision:M was detected, a bunch of information about it was displayed and no error message was returned.  I even used the command lines to send an mp3 file on it.

However, after compiling and installing Gnomad2, i kept getting the message that no jukebox was detected on the USB bus when trying to start the application. 

Anybody has any idea of what might cause this problem?  Thanks in advance.

---

### Post by msak007 on 2006-12-26
When running Gnomad, have you tried running it as root? Chances are it'll detect the device. If it does, then follow the steps below as the problem could in the udev rules, which tell the system who can access what devices. If not, then you have a different problem.

libmtp comes with its own script to copy udev rules to where they need to so you can access the player using Gnomad as a regular user. Navigate to the folder you compiled libmtp from and do ```
sudo sh hotplug.sh
```which will copy the ruleset to the udev folder (/etc/udev/rules.d/) and then do sudo ```
/etc/init.d/udev restart
``` to restart udev. Once you've done that, open Gnomad as a regular user and it should detect the player. Follow the link in my signature if you want a detailed How To on how to get Gnomad to work with MTP players.

---

