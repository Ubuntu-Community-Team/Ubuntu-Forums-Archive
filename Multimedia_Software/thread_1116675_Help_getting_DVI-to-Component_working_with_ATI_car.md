---
title: "Help getting DVI-to-Component working with ATI card"
date: 2009-04-05
forum: Multimedia Software
---

### Post by Comms on 2009-04-05
I'm pretty new to Linux and this problem has been kicking my *** for the last two days.

Here is what I am trying to do: Build a home backup server slash htpc box.

I am using Restore and I loaded up XBMC which works just fine with just an LCD monitor hooked up. Now, I want to hook up this machine to a HDTV through the DVI port. I have an ATI card and the appropriate DVI-to-YPBPR dongle set to the TV's resolutions (480i, 480P, 1080i. It's an older CRT HDTV).

My hardware is: Asus P5V-800MX, Pentium D 805, 2GB ram, ATI 9700 Pro AGP, 2x1TB drives.

This set up works in windows. I've had this PC running windows XP with 1 year old Catalyst drivers and it outputs through the DVI via the dongle to the TV and it works perfectly.

Dongle:
[img]http://img.skitch.com/20090405-qid1qgwtt5e6aspfa8f9rpun36.jpg[/img]

As far as I know, there's nothing quite like Restore for Windows. I'd like to use XBMC or, hell, VLC, to play videos to the TV but I can't get it to work.

Now, again, I am incredibly newbish to linux. I have self-taught myself a bunch during this experience but I cannot figure out the problem. I've looked at similar TV-Out threads but I can't get it to work. All I end up doing is breaking the xorg.conf or something else. I've reinstalled Ubuntu about a dozen times now and I'm ready to throw in the towel and just dualboot Restore/XP.

Any help would be awesome.

---

### Post by Comms on 2009-04-06
Well, I went with the dual-boot option. It's less than ideal but I just don't have the depth of knowledge when it comes to configuring the xorg.conf file.

I would still like to get this working and I've set up a partition with my original install simply to experiment. 

I set up Windows XP MCE and installed Catalyst 9.3 and it worked immediately so clearly ATI's drivers can do this—well, for windows anyway. 

The driver, in Windows, is configured for 1776x1000@30hz (1080i CRT) through the DVI port. How do I make Ubuntu emulate this config?

---

