---
title: "[SOLVED] Cause of severe interlacing?"
date: 2008-01-14
forum: Mythbuntu
---

### Post by debest on 2008-01-14
Well, I've got Mythbuntu set up, and it captures input from my VCR/DVD combo unit through my PVR-350's tuner input.  However, the quality is, while not quite "unwatchable", rather annoying.

I've attached a couple of screenshots taken from MythFrontend.  The results seem the same whether I watch a DVD "live" (through "Watch TV") or if I record it and watch the recording.  It is a scene from Madagascar, when there is a camera pan from left to right, and the zebra is standing up.  As you can tell, the interlacing is pronounced.

Is this a function of the input source?  The effect happens on all video tapes and DVDs, whether purchased or homemade, Macrovision or not.  (There is no problem playing the same media out from the VCR/DVD combo to a television set rather than the capture card.) When I get cable tv hooked up, will the result be the same?  Or is there something else going on?

Looking forward to any suggestions.  Thanks.

---

### Post by browndog289 on 2008-01-14
Hello,

Not sure if this will help but have you tried the de-interlace feature in Mythfrontend?

To use it in Mythfrontend go to Utilities/Setup -> Setup -> TV Settings -> Playback.

Then select Deinterlace Playback and select the algorithm as Bob (2x Framerate).

Then press Next through all the settings until you are back at the menu and try playing again. This works even if you are outputting to a TV or other interlaced device - certainly made my image sharper on TV.

browndog

---

### Post by debest on 2008-01-14
> Hello,

Not sure if this will help but have you tried the de-interlace feature in Mythfrontend?

To use it in Mythfrontend go to Utilities/Setup -> Setup -> TV Settings -> Playback.

Then select Deinterlace Playback and select the algorithm as Bob (2x Framerate).

Then press Next through all the settings until you are back at the menu and try playing again. This works even if you are outputting to a TV or other interlaced device - certainly made my image sharper on TV.

browndog
Thanks, dog!  I love simple solutions!  Why wouldn't that be enabled by default?

Much appreciated!

---

### Post by superm1 on 2008-01-14
> **debest said:**
> Thanks, dog!  I love simple solutions!  Why wouldn't that be enabled by default?

Much appreciated!
Because it takes extra CPU to do, and not everyone has progressive scan monitors.

---

### Post by browndog289 on 2008-01-14
As superm says it uses extra CPU power and linux is streamlined to run on even low end systems, but most decent systems can manage to deinterlace a stream in realtime as you've found out! I'm glad it solved the problem for you! 

Happy MythTV-ing!!

browndog

---

