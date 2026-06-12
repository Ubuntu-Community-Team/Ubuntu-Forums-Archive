---
title: "CA0106 my sound settings is wierd."
date: 2009-03-09
forum: Multimedia Software
---

### Post by j0n3r0ck37 on 2009-03-09
I have sound blaster Audigy SE 24bit with EAX advance HD card and running ubuntu 8.04. I disabled the onboard card through bios and installed ubuntu after that. Here's what it got so far. I whent to system/preferences/sound I set everything alsa except music and movies. But I notice that their is four different CA0106 and found out the third CA0106 down is rear and the fourth CA0106 is front speakers. I figured out that the first two CA0106 is prolly for center speaker and side speakers. Now I am using a 4.1 speaker system and how do i join the third and fourth CA0106 as one setting to use my front and rear speakers at the same time and have it in the mixer volume control to activate the rear controls and the front controls at the same time.

---

### Post by kostkon on 2009-03-12
I think you'll need to better setup *PulseAudio* in your 8.04 (since that in 8.04 *PulseAudio* is not setup the right way) by following [this guide]("http://ubuntuforums.org/showthread.php?t=789578") and then setup your 4.1 by following [this guide]("http://ubuntuforums.org/showthread.php?t=795525").

And the sound playbacks in your sound preferences (i.e. *System &#8594; Preference &#8594; Sound*) must be set to *Autodetect*.

Hope that helps.

---

