---
title: "Freeze on long seeks"
date: 2008-08-11
forum: Mythbuntu
---

### Post by huzzak on 2008-08-11
Hey guys,

I've got Mythbuntu running on an older desktop that I bought surplus from my university.  It has a Pentium 4 processor, 512 MB of RAM, a forty gig hard drive and a PVR-350 tv tuner.

When I fast forward or rewind while watching live tv, the system will freeze and display only a still frame.  I have to restart x to get things going again.  I can pause just fine, it is the seeking that is the problem.  Do you think that it might have something to do with the hard disk access speed?

My other question is about sound.  I guess the sound from the tuner is just being cycled through the tuner card to the television.  Recorded television outputs correctly, but if I want to watch an AVI through VLC, it doesn't send the sound out to the right place.  I'm not sure what would be the correct thing to do here.

Thanks.

---

### Post by newlinux on 2008-08-11
How do you have you sound hooked up to your TV from your sond card (stereo line out, spdif, etc.) Can you watch an avi through mplayer (commandline to see if you get any error messages) or mythvideo's internal player and see if you get sound?

What type of disk do you have? If nothing else works with the fast forward or rewinding you can always do skips (you can set the lengths of forward and backward skips) or direct seek (pressing 30i will take you directly to the 30th minute of the show) as workarounds for now. For me a long time ago I think I used to get some funky behavior with fastforward and rewind and started just using skips and direct seeks. I don't know if I still have problems, as now I always use skips and direct seeks.

---

### Post by huzzak on 2008-09-13
Thanks for the advice.  My remote control doesn't work for some reason (it has power, and is emitting, but isn't being recognized by the computer), but your workaround for seeking has gotten rid of the freezing and locking up problem using the keyboard as the interface.

I purchased some cables and linked up the sound through the computer.  Now everything works as far as sound goes except for DVDs (they only outside of the Mythbuntu interface).  The volume can't be controlled through the computer though, which is weird.  Any idea why that might be?

---

