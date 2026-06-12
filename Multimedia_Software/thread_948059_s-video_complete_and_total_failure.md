---
title: "s-video: complete and total failure"
date: 2008-10-14
forum: Multimedia Software
---

### Post by elustran on 2008-10-14
I have been totally unable to get s-video output to my TV.  This MAY be a hardware problem - I don't even see video when the computer POSTs.  All I'm trying to do is get my monitor output mirrored to my TV like I've always done.

Specs:
athlon x2 5000
nforce 430 chipset
geforce 8600GT

I've tried several things, and I have never gotten so much as a flicker of video on the TV from my s-video port.  I've gotten fuzzy unsynchronized video using a DVI-svideo converter, but that's about it.  

I've tried two different video cards (both 8600s, admitedly).  I have tried mucking around with a few xorg.conf settings to no avail.  I'm not sure I can recount the various settings I've tried.  I have tried different drivers, including the nv driver.  The few guides I've seen on getting TV output working mostly seem to cover using your TV as a second monitor - I haven't fully tried them because I'm not looking for a solution that complex.

My fundamental question is this:
Should I see video when the computer POSTs, or is there something funky going on with the new nvidia cards where I need to activate svideo via the drivers?

I'm looking for ANY ideas that might help narrow down my problem.

---

### Post by overdrank on 2008-10-14
> **elustran said:**
> I have been totally unable to get s-video output to my TV.  This MAY be a hardware problem - I don't even see video when the computer POSTs.  All I'm trying to do is get my monitor output mirrored to my TV like I've always done.

Specs:
athlon x2 5000
nforce 430 chipset
geforce 8600GT

I've tried several things, and I have never gotten so much as a flicker of video on the TV from my s-video port.  I've gotten fuzzy unsynchronized video using a DVI-svideo converter, but that's about it.  

I've tried two different video cards (both 8600s, admitedly).  I have tried mucking around with a few xorg.conf settings to no avail.  I'm not sure I can recount the various settings I've tried.  I have tried different drivers, including the nv driver.  The few guides I've seen on getting TV output working mostly seem to cover using your TV as a second monitor - I haven't fully tried them because I'm not looking for a solution that complex.

My fundamental question is this:
Should I see video when the computer POSTs, or is there something funky going on with the new nvidia cards where I need to activate svideo via the drivers?

I'm looking for ANY ideas that might help narrow down my problem.
Hi and have you tried setting the tv up using nvidia-settings?
You may also try and use the command using the alt, F2 keys and enter the command ```
gksu displayconfig-gtk
``` and setup the extra monitor there.

---

### Post by elustran on 2008-10-15
> **overdrank said:**
> Hi and have you tried setting the tv up using nvidia-settings?
You may also try and use the command using the alt, F2 keys and enter the command ```
gksu displayconfig-gtk
``` and setup the extra monitor there.
Yeah, I tried it - all it wound up doing was killing anything that did work, but that was mostly settings.  Eventually I'm just going to reinstall, but that might not help.

I've read that the latest nvidia Windows drivers have been nasty to deal with due to leaving out some proprietary decoding or somesuch.  That -might- have some bearing on the problems with our linux drivers.  At the very least, it indicates to me that s-video out might not work like I'm used to.

Really, what I'm trying to gauge here is whether or not s-video should be working like I'm used to - should I see it work when the computer POSTs?

---

### Post by fenian on 2008-10-15
Yes it should show up on the TV when the computer posts ,but if you havent set up your xorg.conf it will switch to noise as Ubuntu begins to boot.

---

### Post by elustran on 2008-10-15
How much can I curse on these forums without getting modded?  

Looks like the nforce 430 chipset can only handle 1 analog video stream at a time, and it turns out that the VGA monitor I had connected through a DVI adapter was one of those streams.  It took some digging to figure that out - I wish it was in bright red letters on the ******* cover.

I unplugged the VGA and the video went to my TV just fine.  It kinda sucks that the chipset is limiting the abilities of my card, but that's what I get for buying a cheapo mobo.

Now it's time for tweaking.

---

