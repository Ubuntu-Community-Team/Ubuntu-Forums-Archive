---
title: "Help With USB Audio Interface"
date: 2015-05-06
forum: Multimedia Software
---

### Post by lamogo on 2015-05-06
Just got my Edirol USB UA-101 today, and got it working OOTB on Uubuntu Studio but want to use this on my KDE desktop mostly.

I've plugged the device and it is seen by the computer, and appears that ALSA is loading the correct module. However, when I go to AV Settings the device is not shown for set up. I see it in alsamixer but not in my settings panel. Not sure what to do next, any insight would be great, thanks!

---

### Post by lamogo on 2015-05-07
Still no help?

After so more research I think that Pulse was not recognizing the device. I installed the KXStudio repos and installed their version of the sound applications. In Phonon the device is there but it says it doesn't work and returns to the default audio device. I am, however, able to open Audacity and select my device from the ALSA group and record and play back on it. It is a temporary fix, I just record with it, and play back through the default so I don't have to switch speakers but hope someone can help me get this fixed right so KDE can use it for all applications. Thanks.

---

### Post by Bucky Ball on 2015-05-07
*Thread moved to **Multimedia**.*

You may have more luck here as your support request is not related to ***Desktop Environments***. Good luck.

PS: It doesn't sound like you're using Jack at all. Launch Jackctl (if you have it installed) and see if it shows up there. You may need to tweak the ins and outs and routing.

If it works OOTB in Studio, perhaps look for the difference. What app were you using it with OOTB and how did you have the sound routed/setup? What app are you using in Kubuntu?

It's a big step, but you could install ubuntustudio-audio from the repos and see if that does it ...

---

