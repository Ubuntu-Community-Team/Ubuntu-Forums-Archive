---
title: "What just happened to my sound?!"
date: 2009-12-28
forum: Multimedia Software
---

### Post by Objekt on 2009-12-28
For absolutely no reason, I'm now getting sound only on the left in both Kubuntu 9.04 and Ubuntu 9.10.  It started out of nowhere about an hour ago, and has persisted through several reboots & power cycles.

I can't fix it, considering I did nothing to cause it, and have no idea why it happened.  What the hell is going on, and how do I fix it?  

Sound works fine in Windows XP, so I know there's nothing physically wrong with my speakers, soundcard, cables, etc.

FWIW, I checked in Alsamixer, and no, nothing is muted ,and the volume level is exactly the same for both channels.

UPDATE:

It seems to be something particular to my hardware, which is a Creative Labs Audigy ZS2.  There is a mixer item called "Audigy Analog/Digital Output Jack" which MUST be turned on, or you will only get muffled sound on the left side.

You also have to have the item called "Tone" unmuted, or sound will be tinny and quiet.

I think this is solved, and can be archived for others who stumble into this problem in the future.  Going to do a few more tests before I mark it "SOLVED."

Tests complete - it's all working now.  Marking this one "solved."

---

