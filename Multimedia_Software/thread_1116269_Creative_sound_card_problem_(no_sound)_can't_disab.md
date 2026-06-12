---
title: "Creative sound card problem (no sound) can't disable onboard sound"
date: 2009-04-04
forum: Multimedia Software
---

### Post by PallyofAwesome on 2009-04-04
Hi, I'm a new to Linux, just installed yesterday - currently running Ubuntu 8.10. I installed Amarok and tested some of my songs to make sure they work - everything went fine. When I booted up this morning I wanted to get some new games on here and, after installing Battle for Wesnoth, realized my sound wasn't working. I opened up Amarok again and none of my songs would play. I started doing some internet searches and read probably 15+ guides/threads about setting up the default sound card and disabling the onboard sound in the BIOS. 

using ```
less /proc/asound/modules
``` I can see that I managed to get snd_ca0106 priority over snd_hda_intel. This is what I want. After rebooting I noticed I hear the login sound, but after that nothing. I tried to go into the BIOS and disable the onboard sound but I couldn't find an option for it - just a bunch of USB and SATA options in there. I tried doing a few other suggested steps from the guide on these forums and some other sites, but now I lost track of what I was doing and I have no sound at all (not even the initial login screen). 

Any help on the matter would be appreciated. I'm going to be trying to figure out the issue in the mean time. Thanks in advance.

---

