---
title: "VLC doesn't save ALSA configuration, problems result"
date: 2008-05-09
forum: Multimedia Software
---

### Post by the2ndgenesis on 2008-05-09
Hey everyone. I've been having some trouble with the audio configuration of my VLC player, and was wondering if anyone has had similar trouble. Currently it only plays audio through my headset, regardless of whatever my default sound card is set to at the time.

Long story short, I've tried to set my VLC audio output module to ALSA in preferences -> audio, and set the device to my laptop's sound card instead of the headset, but this ultimately doesn't do anything. I've noticed that even when I click "save settings," the audio module settings all go back to the default when I close and re-open the player. It's really become quite bothersome, which is a shame because I've loved VLC ever since Windows.

Has anyone noticed any similar issues with VLC, or does anyone have any advice to offer for this problem?

Included is a .jpg of my laptop's physical specs, if that helps any.

---

### Post by the2ndgenesis on 2008-05-09
Interesting, if not confounding, development:

Apparently after unplugging/replugging my headset, VLC decided it wants to run from my speakers all of a sudden. My current sound card is set to my headset, though, and all other applications run as expected from my headset. When I opened up the sound preferences to get a look at them, I found that they're exactly the same as they were before, when the audio came only through my headset. Puzzling indeed.

Is there some kind of configuration file for VLC that I can edit manually to alleviate some of this craziness?

---

