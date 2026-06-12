---
title: "Any simple suggestions for wireless usb adaptors?"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by confused old guy on 2010-07-11
Hi everyone.  I am brand new to Ubuntu on a laptop (been using it on desktops for some time).  After having installed Lucid on that my Dell Latitude E5400, I found I had one of those Broadcom wireless cards that does not work well with Ubuntu.  I tried a few fixes from the forums but they did not work.   I figured that rather than trying to solve the problem, I could just go out and buy a simple USB wireless adaptor at my local Staples.   But after a bit of reading, it seems this can be tricky too.   Yes, I looked over a lot of the wireless material in the forums, but hope to avoid  having to worry about chipsets and ndswappers and the many wireless  problems people talk about in the forums.  Can any one suggest a few USB wireless adaptors that are easily available and work out of the box with Lucid?  It would be much appreciated.  Confused.  :D

---

### Post by bkratz on 2010-07-11
> **confused old guy said:**
> Hi everyone.  I am brand new to Ubuntu on a laptop (been using it on desktops for some time).  After having installed Lucid on that my Dell Latitude E5400, I found I had one of those Broadcom wireless cards that does not work well with Ubuntu.  I tried a few fixes from the forums but they did not work.   I figured that rather than trying to solve the problem, I could just go out and buy a simple USB wireless adaptor at my local Staples.   But after a bit of reading, it seems this can be tricky too.   Yes, I looked over a lot of the wireless material in the forums, but hope to avoid  having to worry about chipsets and ndswappers and the many wireless  problems people talk about in the forums.  Can any one suggest a few USB wireless adaptors that are easily available and work out of the box with Lucid?  It would be much appreciated.  Confused.  :D

A lot of people use the Broadcom devices with much success. If you do a

lspci -nn

in terminal and look for the network controller and it says "BCM4312" you might try this posting.


[http://ubuntuforums.org/showpost.php?p=9134672&postcount=6](http://ubuntuforums.org/showpost.php?p=9134672&postcount=6)

Heard good things about it.

---

### Post by gordintoronto on 2010-07-11
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

