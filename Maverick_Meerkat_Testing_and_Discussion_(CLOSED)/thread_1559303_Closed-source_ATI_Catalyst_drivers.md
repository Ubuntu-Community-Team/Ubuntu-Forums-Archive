---
title: "Closed-source ATI Catalyst drivers?"
date: 2010-08-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by christian.convey on 2010-08-23
Anyone know when the closed-source ATI Catalyst drivers are likely to be available?

I have a Radeon HD 4850 for which I'd like to use the closed-source driver.

---

### Post by pulpo69 on 2010-08-23
i also would like to know it.

---

### Post by alphacrucis2 on 2010-08-23
[URL="http://ubuntuforums.org/showthread.php?p=9746957"]http://ubuntuforums.org/showthread.php?p=9746957
[/URL]

Looks like it's no dice yet. Catalyst 10.8 should be out in a few days so keep your fingers crossed;)

---

### Post by ToxicBurn on 2010-08-23
should i not even bother with ubuntu then ?

I have a HD 5770 and i need full 3D support for Games

---

### Post by alphacrucis2 on 2010-08-23
> **ToxicBurn said:**
> should i not even bother with ubuntu then ?

I have a HD 5770 and i need full 3D support for Games

Use Ubuntu 10.4 LTS then. Maverick is still in alpha testing and it is quite normal for there to be problems with proprietary drivers during release testing.

---

### Post by Zorgoth on 2010-08-23
> 
should i not even bother with ubuntu then ?

I have a HD 5770 and i need full 3D support for Games


ATI Catalyst 10.7 works fine for me and my little ATI Mobility Radeon HD 5470.  Should hopefully work for you too, but I don't know.  I have lots of Windows games working:

e.g.
WoW
Starcraft II
Half-Life 2
Civilization IV
Europa Universalis III
Majesty 2

Mount and Blade: Warband sort of works but is awfully hard to play because of a mouse bug, and I can't get Global Agenda to run.

EDIT:  Looks like it is a particular thing to do with an X.org update.  Don't know if it is Ubuntu 10.04 or just the development version.  Even if the update is installed on 10.04 by default it should be pretty easy to downgrade until ATI fixes things up.  It's normal that ATI lags behind X.org updates, and it does not mean ATI does not work on Linux.  One thing to note about Windows games on Linux is that the graphics workload isn't too much heavier but there is a huge amount of CPU overhead, so if you want to play games via wine, you should have a pretty powerful CPU.  I have a Core i7-720QM and most games run without huge performance hits, but clearly in some cases even with my relatively weak graphics card and strong CPU the CPU is the main bottleneck.

---

### Post by andrek on 2010-08-24
Catalyst 10.8 is about to be released tomorrow. I hope this will fix the x-server 1.9 incompatibility.

---

### Post by ELD on 2010-08-24
> **ToxicBurn said:**
> should i not even bother with ubuntu then ?

I have a HD 5770 and i need full 3D support for Games
<snip> This version of ubuntu is of ALPHA quality.

---

### Post by ToxicBurn on 2010-08-24
> **ELD said:**
> <snip> This version of ubuntu is of ALPHA quality.

First off ELD no need to get RUDE ,

I need 3D support that is not Stupid 

I know this is Alpha that is the reason i am here in the forums 
I also like to test things like Wine and I work close with others that play world of warcraft and other games in linux
next time you want to be rude dont do it on these forums please

---

### Post by ranch hand on 2010-08-24
I think the choice of working could have been better but what you seem to be saying is that this will be your only installation.   *snip*

I am on 10.10 right now as I am all day every day.  I am using it as a "production" OS.  I also have several other installs of 10.10 on this drive to make sure one works.  There is also an install of 9.10 and 10.04 so that I can fix 10.10 if all of them go down.

None of these 9 installs is my actual main installation.  This is an external usb enclosure with two 320Gb drives in it.  Used only for testing the current dev version of Ubuntu.

My main OS, which I will be switching to for the night very soon, is on an internal drive that is turned off in bios to isolate it from these testing installs.

At that, I am not completely sure that I am not being stupid to have the testing installs on the same box as my main OS.

There is no need for any particular functionality in the test OS', in any way, prior to the last week of the beta cycle and the RC cycle.  To expect anything to work from day to day is crazy before the RC.

I think this is the message that was intended.  This is an Alpha.  You do not need 3D.  If you can achieve that, and maintain it, Great.  If not, what you "need" is too file bugs and get it fixed.

That way it is reasonable, for ALL users, to "need", and indeed expect, 3D to work when 10.10 Final is released.

I do not think rudeness was intended.  We do get a little too blunt at times on this forum but most of us expect that (rarely and very occasionally) from time to time as stress builds up during the cycle.  Many of us have been at this, with 10.10 since 5-6-10.  We are getting a leettle techy.  Please try to take us with a large grain of salt.

---

### Post by ELD on 2010-08-25
Since my post got removed, to be clear it was not meant as an insult and i apologise.

I don't think your stupid and i'm not meaning in any way to be rude BUT i think to expect ATi catalyst to work with an Alpha version is. Ubuntu devs can't change that, no distro dev can only ATi can make it work.

As stated before if you really NEED it use 10.04, that's the stable one.

Your best bet is to dual boot the stable and dev versions together, it's exactly what i do to test but also to have a stable environment when i need it.

---

### Post by jou770d on 2010-08-25
[http://www.phoronix.com/forums/showthread.php?p=144201](http://www.phoronix.com/forums/showthread.php?p=144201)

Catalyst 10.8 is out.
I'm still downloading it myself. However, judging from the comments on phoronix, it seems we're in for yet another disappointment from ATI with no proper support for xserver 1.9.

Edit:
I seem to be blind, somehow I missed the existence of this thread here:
[http://ubuntuforums.org/showthread.php?p=9745702](http://ubuntuforums.org/showthread.php?p=9745702)

---

