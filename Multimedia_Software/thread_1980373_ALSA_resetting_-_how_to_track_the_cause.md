---
title: "ALSA resetting - how to track the cause?"
date: 2012-05-15
forum: Multimedia Software
---

### Post by theScarletManuka on 2012-05-15
My laptop initially had no sound through the speakers, but I generated a patch using the HDA Analyser tool which I run on boot from rc.local. This worked nicely on Mandriva, and seemed good after moving to Ubuntu 12.04

After a few days I have found that the sound sometimes cuts back out.  When I re-execute my patch file it comes back, which makes me think that something is resetting ALSA.

Please advise where I might look for traces of whatever might be causing the reset.  There certainly isn't anything in /var/log.

I would also be interested to know whether running the patch from rc.local is my best choice, and how I might pass my patch on for adjustment of the ALSA source by somebody who understands what it does.

Thank you,
Martin.

---

