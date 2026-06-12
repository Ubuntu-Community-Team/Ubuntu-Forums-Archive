---
title: "Mixvibes U-Mix 44 .asoundrc configuration"
date: 2011-12-29
forum: Multimedia Software
---

### Post by Drakmor on 2011-12-29
Hey all, I recently got a Mixvibes U-Mix 44 USB sound card for use with Mixxx. It is detected in kubuntu, but playback does not work very well. I first thought it was a hardware/ Mixxx compatibility problem, so I posted it on the Mixxx forums ([http://mixxx.org/forums/viewtopic.php?f=3&t=3182).]("http://mixxx.org/forums/viewtopic.php?f=3&t=3182") However, it is apparently a software issue.

I need to set up my .asoundrc file specifically for my card, and I honestly have no idea how to do it, even after a few hours of research. There are 4 channels on the card, channel 1, 3, and 4 are for general output, and channel 2 is for monitor/ cueing. 

I'm pretty sure I need to combine the different channels into two different virtual cards ([http://alsa.opensrc.org/.asoundrc#Joining_devices_to_make_multichannel](http://alsa.opensrc.org/.asoundrc#Joining_devices_to_make_multichannel)), but I couldn't figure out the syntax to get it to work. 

The ideal end result for this would be two virtual cards: One for the master output with channels 1, 3, and 4, and one for cueing with channel 2. 

Any chance anyone could give me some pointers on how to set it up? Thanks!

---

### Post by Drakmor on 2011-12-31
No idea what I did differently from my post in the Mixxx forums, but it works now without any .asoundrc config.

---

