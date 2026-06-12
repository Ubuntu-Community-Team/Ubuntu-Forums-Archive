---
title: "Mythbuntu 10.10 Sound Cuts Out"
date: 2010-11-04
forum: Mythbuntu
---

### Post by srmcatee on 2010-11-04
I have a system that I was running Mythbuntu 8.x on just fine.  I just did a full install upgrade to 10.10.  Everything is working except the sound will cut out for 2 seconds while watching video.  The speakers also constantly have a random chirp or crackle.

I also noticed that if I watch youtube video in Firefox I get the same problem.

I am setup with an onboard sound card using digital.  I am only using ALSA:default in my sound settings.  I put out the sound through my digital cable in the back of my pc.

Any ideas what is causing this or how to fix?

---

### Post by yonkiman on 2010-11-10
I've been battling a similar problem random (S/PDIF glitches that cause a 1-2 second soubd dropout as my receiver re-syncs) with MythBuntu since 8.04.  Upgrading to 9.10 didn't help.  I finally bought a new soundcard (Asus Sonar DS).  It performed MUCH better once I got it working, but would still have the occasional sound dropout.  And it took a while to get it working - supporting that soundcard needed a newer version of Alsa than mythbuntu was using, so I had to use the excellent Alsa upgrade script (search this forum to find it) to get that going.  But it got rid of 95% of my problem.

So one suggestion (if all the software/setup fixes fail):  Buy a cheap soundcard with a chipset Ubuntu has had supported for a long time.

Good luck!

---

