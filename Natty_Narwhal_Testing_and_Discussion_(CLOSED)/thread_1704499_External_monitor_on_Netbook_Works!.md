---
title: "External monitor on Netbook Works!"
date: 2011-03-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2011-03-10
Acer Aspire one netbook has 1024x600 screen.  As of today, external monitor at 1280x1024 works on both Unity 3D and Classic no effects!

That is, as of linux-image 2.6.38-6 and 10 March update & safe upgrade.  It was busted big time a couple days ago.

Now Natty booted up in some weird 800x600 mode mirrored on both screens.  This was workable enough to get to the Monitors application, turn off mirroring, turn off laptop screen, set external monitor to 1280x1024. 

Jerry

---

### Post by Kobalt on 2011-03-11
Is your netbook sporting the Intel GMA 950 ? I've been waiting for this to work for a long time :)

---

### Post by jerrylamos on 2011-03-11
Well if I do:

lspci | grep VGA 

I get

Intel Corporation N10 Family Integrated Graphics Controller

whatever that means.

This netbook was built in November 2010  so I think it is pretty well the latest Intel had at the time.  Seems to run Unity O.K., at least the parts of Unity that are functional.

Now I don't like Unity but I'm testing whatever Ubuntu has in Alpha so I run it anyway.

I might add I split the 250 GB hard drive between Windoze 7 and Ubuntu Maverick.  Windoze is sluggish however Acer has some custom software for it so I keep it.  

Natty I've got on a USB Hard Drive along with Maverick and a archive partition.  It's an old laptop drive in an inexpensive USB case.  Runs nice and fast.

Natty is installed on the USB Hard drive so Natty Grub will screw around with the USB hard drive and hopefully leave alone the 250 GB hard drive with Windoze.  After Natty updates run grub and mess things up I run Maverick grub on the same hard drive to straighten things out. 

Now with Ubuntu, the 1.66 gHz Intel has quite good performance.  Apparent screen response is similar to my fast desktop.

Anyway I'm having fun with Alpha 3 linux-image-2.6.38-6.  Alpha 2 was hardly usable.  And of course Classic no effects is faster and easier for me.

Jerry

---

