---
title: "Very low volume on mic input"
date: 2006-03-11
forum: Multimedia &amp; Video
---

### Post by The Belgain on 2006-03-11
Hi there,

I'm trying to set up my headset to be able to use it with openwengo for VoIP calls.  I'm having trouble with the mic input though.  Testing it in the 'Sound Recorder' application, it does record sound, but at an extremely low volume (I need to turn the playback volume right the way up to hear it at all).

I've set the volume for the mic input to the maximum under the volume contol for the system.  The sound card used is an onboard Intel ICH6, using ALSA.

Any ideas?  Is there some kind of mic boost I can turn on here?  Has anyone else had this problem?

---

### Post by ookami on 2006-08-05
I have the exact same problem (after finally getting the mic to work at all!) with the built in sound on my nforce2-chipset.

---

### Post by The Belgain on 2006-08-05
Well, I never did solve this problem.  However on my laptop, with Dapper, this works fine (volume is at a sensible level).

Oh well...

---

### Post by paganini on 2006-10-18
There's something that does exactly what you need. It's called "Mic Booster", and can be set using the mixer control program.

Open "alsamixer" and scroll right to the "Mic Boost" bar. It may not be a bar, but rather a little square. When the red chevrons are over it, type "m" (on the keyboard). The "MM" will become "OO" and your Mic should work now.

---

### Post by ookami on 2006-11-12
I have the same problem as the original author with my nforce2-chipset sound. Usin the "Mic boost" didn't help much but it's a little bit better now. Still totally unusable for VoIP though.
When under windows on the same computer I can have the headset just standing beside my computer and it records fine, in Ubuntu I have to almost eat the mic to get any result.

---

### Post by zeroseven02 on 2007-02-09
Try opening alsamixer, then press tab and it might take you to another device with capture settings.  On my card they were disabled but after I increased the capture volumes it enabled a mic boost and now my mic works fine.

---

