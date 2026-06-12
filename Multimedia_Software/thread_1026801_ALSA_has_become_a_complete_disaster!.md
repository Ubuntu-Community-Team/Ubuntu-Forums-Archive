---
title: "ALSA has become a complete disaster!"
date: 2008-12-31
forum: Multimedia Software
---

### Post by sonicb00m on 2008-12-31
I never used to have major sound issues but ever since the last few weeks with intrepid something has sneaked in the back door causing me major headaches.

Originally I ran an 24/96 Terratec sound card and a USB phone. A combination that worked pretty much flawlessly for the last 2 years.

I upgraded to Intrepid early beta stage and did a fresh install when it came out. No problems at all.

After a few weeks the 24/96 stopped working completely and the USB Audio continued to function. I tried reinstalling alsa and following a load of the guides but nothing would get it working again. I figured it might be broken but I booted to an old Hardy partition and it worked flawlessly. 

Eventually I gave up and whipped it out and enabled the Intel onboard sound card. The ALC662. It never ever had any problems. This card wouldn't work either so i followed a guide to recompile alsa specifically for the card. That got the card going but the usb audio was no longer working (it doesn't even appear in the sound settings). I tried to recompile with the snd_usb_audio switch (or somethign like that) and it wouldn't play ball, only stopping the intel from working again. 

I gave up at this point and reinstalled Intrepid from scratch downloading it again from the Net. THe 24/96 still wouldn't work but intel and the usb does ...sort of. 

The intel is working most of the time except often when i run totem there is no sound coming out of it. The volume control is also greyed out. 

The usb phone will not play anything unless I switch the output to OSS then it's ok. "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback."

Sometimes MPD stops working and complains it can't hook onto the alsa slave.

What is going on with my audio? It's become exasperating! I can't face another reinstall. This is as close to a fresh system as can be!

---

### Post by markbuntu on 2008-12-31
Extensive troubleshooting and set up help for Hardy and Intrepid is here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by sonicb00m on 2008-12-31
THanks but as already stated I've been through these. I've had a flawless audio system for 2 years but something in the last few months/weeks has started to cause problems with my system. For something that worked out of the box with no interferring it makes no sense to suddenly rely on old guides to get alsa working. I want to know what has gone wrong.

---

### Post by sonicb00m on 2009-01-03
it's the bloody pulse audio that has been causing the problems again. This time I totally removed it. I wish they never put a project in there that isn't even working properly. Insanity. Great in theory but poor in exection right now.

---

