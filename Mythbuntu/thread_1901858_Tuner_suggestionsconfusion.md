---
title: "Tuner suggestions/confusion"
date: 2011-12-29
forum: Mythbuntu
---

### Post by nightwar on 2011-12-29
Hello.

Ive been using mythtv for the last 3 years. I have a PVR150 and PVR350.

I have time warner cable.

My goal, i want to be able to view local channels channels,and the HD channels in what i am going to assume is clear QAM. 

Is there a disney-hd channel, like example ch#: 48-1, like therer is a nbc channel 3-1?

If so how would i tune this with mythtv? 

I also have a samsung STB from them with a firewire port, and have had no success with this so far.

For the HD homerun box, does that only get the local OTA channels?

Ive read lots about tuners,qam,etc. I think i am just getting confused as to what im looking for.

thanks

---

### Post by agamotto on 2011-12-30
Hallo, I think I can be of some help with your issues/questions.

You can indeed use the HD Homerun series to view your Clear-QAM cable channels.  However, many, if not most, cable operators are scrambling their HD 'premium' channels.  You will be able to view your local HD OTA pass-through channels, but things like HD SyFy, CNN, etc... will most likely be encrypted.  Our local provider dumps all of the Clear-QAM channels in the 51-x to 56 range.

Yes, your channels will show up as 3-1, or 43-4.  However, depending on your provider's stability, your digital channels might move around if they decided to reassign them at a whim.

To 'tune' them in, you would simply choose to record 'program' on channel 'x-x'.  In the case of live tv, it would be choosing 'x-x,' which will usually smoothly change you from your analog input to digital input.

The STB is probably the biggest indication that your provider is encrypting channels.  Anything that requires the STB to view will not be watchable with just your tuners.  To view these 'encrypted' channels, you will have to plug the output of the STB into your tuner of choice.

The HD Homerun boxes will get any unencrypted digital channels that your 'input' provides.

I hope this clears some of the questions up!

---

### Post by LowSky on 2011-12-31
You can look into cablecard options for watching all of your channels, but even then those options can be tricky, the DRM can make viewing a nightmare even then.

The best option is a hauppauge HD PVR hooked up to the cable box, and then use a ir blaster or firewire control to change channels.

---

### Post by nightwar on 2012-01-04
i understand this now thanks.. bottom line, if you have time warner with mythtv you will only be able to do SD, unless you want the stations like NBC,ABC,CBS,etc...

The hd-pvr solution is the only option to indirectly do HD.

My question about the hd-pvr is what is the CPU/usb bandwidth load on the CPU.  i wish they had a linux compatible card. (they have one, no linux drivers)

---

