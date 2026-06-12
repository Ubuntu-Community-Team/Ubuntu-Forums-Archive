---
title: "underperfoming graphics 11.04 with ati drivers"
date: 2011-08-31
forum: Multimedia Software
---

### Post by sodariver on 2011-08-31
hi, first off, i am a noob to ubuntu. i am trying to get some decent graphics out of my ati Mobility Radeon HD 5430, there is no way i can do this without the proprietary driver (unity won't even run without it). then, i tried pretty much everything to get a decent experience, say while working with the blender game engine: 

I installed the driver and followed the instructions here-> [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)

i have disabled the vBlank in the OpenGL settings in CompizConfig, also in the Composite options, i disabled the "detect refresh rate" and set it manually to 60.

on the ati control panel there is a give and take situation: if I enable the "tear free" option, the graphics are better, but slower, whereas when it's disabled the graphics run faster, but well, teared.

do you guys have any ideas? i hate to say this but the realtime video performs better in windoze :( i hate it so any help will be very welcome.

---

### Post by Johnny Buffalkill on 2011-09-03
I usually just post replies to the 11.04 - ATI proprietary graphics  issues to commiserate.  I still haven't got them working at all with natty, but my GPU is an HD 3200, so I don't miss as much by using the open source drivers, and I mainly watch movies and don't play games much.

That said, I did run across a site that seems to imply that upgrading the kernel to 2.6.39 may allow the proprietary drivers to work with natty.

[http://www.mindwerks.net/2011/04/ubuntu-11-04-natty-with-fglrx-and-2-6-39/](http://www.mindwerks.net/2011/04/ubuntu-11-04-natty-with-fglrx-and-2-6-39/)

I have *not* had a chance to try this yet so I can't verify whether it works or not.  The instructions seem to be written for the 64 bit version, so there may need to be changes for 32 bit.  Furthermore, I'm home alone with my kids now so my reading comprehension is severely impaired - its possible I'm misinterpreting what this is supposed to do.  I'll eventually give this a try and report back, unless a better answer appears.

---

