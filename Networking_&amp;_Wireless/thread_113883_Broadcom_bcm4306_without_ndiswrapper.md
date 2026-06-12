---
title: "Broadcom bcm4306 without ndiswrapper"
date: 2006-01-07
forum: Networking &amp; Wireless
---

### Post by julipanno on 2006-01-07
I was pretty sure that upon installing Breezy (about two months ago), my broadcom bcm4306 wifi worked out of the box without having to install the ndiswrapper like I had to in Hoary. Not needing the wireless connection until now I had it deactivated, but now I seem unable to reenable it (i.e. wlan0 does not exist anymore). "lshw -C network" reveals the card as UNCLAIMED. I tried modprobing the ipw2200, but nothing seems to happen.

I have searched around the ubuntuforums for a solution, but all of the how-to's for the broadcom bcm4306 includes ndiswrapper, and many claim that my card won't work without it. I have no recollection of downloading the windows-drivers or configuring ndiswrapper in Breezy, and therefore I hesitate to do in case a solution without proprietary drivers exists.

So I begin to question my memory, and what I am asking for is this: Is it possible  that my broadcom bcm4306 worked out of the box when I first installed Breezy or is this memory just a construct of my mind?

Peace,
Stian

---

### Post by zahidism on 2006-01-07
is there even a wireless driver that isnt a driver wrapper of a windows driver natively in ubuntu?  i doubt it.  but then again i know nothing.  my broadcom bcm4306 (dell wlan 1350) required the driver and ndiswrapper (after about 3 hours i figured out my compiling of ndiswrapper was wrong) to get it going but now it's rock solid.  anyway, i really don't think there is such a thing i mean i know breezy *might* come with ndiswrapper but there's no way it came with the driver.    that's just my 2 cents.

-z

---

### Post by Lambert on 2006-01-07
[quote=julipanno]I was pretty sure that upon installing Breezy (about two months ago), my broadcom bcm4306 wifi worked out of the box without having to install the ndiswrapper like I had to in Hoary[/quote] 
If it is broadcom, it didn't work out of the box in breezy as it doesn't come with a native driver for wireless broadcom chipsets.

There is a driver coming for broadcom which is very experimental currently and you have to have a 2.6.15 kernel for it to work.

> I tried modprobing the ipw2200 
Not sure why you would try this module as it's for an intel 2200bg chipset. If it is broadcom then you  need ndiswrapper.

[quote=zahidism]is there even a wireless driver that isnt a driver wrapper of a windows driver natively in ubuntu[/quote] 
There are actually a number of native drivers for linux that are not a "wrap" around a windows driver. The only wrapper is ndiswrapper so if that's not being used and device is functioning, it has a native linux driver.

---

### Post by bettlebrox on 2006-02-24
>There is a driver coming for broadcom which is very experimental currently and you have to have a 2.6.15 kernel for it to work.

Lambert do you have any other info on this driver?

---

### Post by Lambert on 2006-02-24
What else do you need to know?

Project home page
[http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

The dapper forum section has some good information.
[http://ubuntuforums.org/search.php?searchid=3996148](http://ubuntuforums.org/search.php?searchid=3996148)

ubuntu wiki page
[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

I use an atheros device so my knowledge is limited to what I read.

---

