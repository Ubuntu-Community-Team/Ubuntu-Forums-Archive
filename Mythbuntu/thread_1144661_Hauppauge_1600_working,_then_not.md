---
title: "Hauppauge 1600 working, then not"
date: 2009-04-30
forum: Mythbuntu
---

### Post by mookie60 on 2009-04-30
old dell 2.3ghz
512 ram
mythbuntu 8.10
nvidia geforce 6200
hauppauge 1600


After the initial learning curve, things were performing well for analog SD recording.  The problem of "losing" the card, and needing to restart it as v4l then switch back to mpeg, was an occasional pain - but it worked.   The digital tuner has been unusable, seems to be poor sensitivity as has been noted by many in this forum.   Overall though, the analog SD recording exceeded my expectations.

This has been the case for almost 2 months, then today the tuner stopped working.   Myth finds the card, and sets it up as MPEG, and the channel scan locks in on the usual (analog cable) stations (though many channels are duplicated in the list).   When attempting to view (or record), the channels are essentially not there.  The channels which are there are mostly static, unwatchable, and unrelated the Schedules Direct listing - it's like being in a rural area and attempting to watch tv with rabbit ears.  

There have been no known power surge events.  Putting the tuner in a different PCI slot hasn't helped.     Direct viewing (bypass myth) through the tv confirms the cable source is ok.


Any suggestions on how to easily determine if the tuner has died.

Thanks for any assistance,

John

---

### Post by klc5555 on 2009-05-01
> **mookie60 said:**
> old dell 2.3ghz
512 ram
mythbuntu 8.10
nvidia geforce 6200
hauppauge 1600


After the initial learning curve, things were performing well for analog SD recording.  The problem of "losing" the card, and needing to restart it as v4l then switch back to mpeg, was an occasional pain - but it worked.   The digital tuner has been unusable, seems to be poor sensitivity as has been noted by many in this forum.   Overall though, the analog SD recording exceeded my expectations.

This has been the case for almost 2 months, then today the tuner stopped working.   Myth finds the card, and sets it up as MPEG, and the channel scan locks in on the usual (analog cable) stations (though many channels are duplicated in the list).   When attempting to view (or record), the channels are essentially not there.  The channels which are there are mostly static, unwatchable, and unrelated the Schedules Direct listing - it's like being in a rural area and attempting to watch tv with rabbit ears.  

There have been no known power surge events.  Putting the tuner in a different PCI slot hasn't helped.     Direct viewing (bypass myth) through the tv confirms the cable source is ok.


Any suggestions on how to easily determine if the tuner has died.

Thanks for any assistance,

John

Sometimes I've noticed that for extended periods the cx18 module simply refuses to load cleanly at boot. Even from a cold boot. When this happens, sudo rmmod cx18 followed by sudo modprobe cx18 gets it going properly.

But the only time I've ever had tuner cards flat-out stop tuning properly, the culprit turned out to be mythconverg corruption, rather than card trouble, after I screwed up in adding a slave backend to the network. To see whether your case is the card or the software, you probably should test your card without mythtv in the way. For the analog side of the 1600, any of the little pvr 150 utilities ought to be able to help you test whether you can get a viewable signal out of your card. I've used KtvTune for this purpose when I couldn't initially get mythtv to configure the 1600; I suppose other little utilities like ttv will do the same. 

The point is if you can get a viewable signal through one of the various little analog applets, then the problem is not the card, it's software. If the card can't get a signal through some applet viewer, then the card itself is likely hosed.

---

