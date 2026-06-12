---
title: "adjusting volume in hydrogen"
date: 2009-09-29
forum: Multimedia Software
---

### Post by Rhetoric Camel on 2009-09-29
I have just installed Hydrogen on my computer so I could make a few drum beats for a few guitar tracks I have. I adjust my volume through my keyboard so my main speaker is set to a certain volume. It seems no matter how low I turn it (even all the way down to mute) the volume of Hydrogen doesn't go down at all. Is there a way to fix this? I know I could just turn my main speaker volume down and it would work but I'd like to be able to turn it up and down with my keyboard.

System>Preferences>Sound>Devices>Default Mixer Tracks
Playback: CA0106 - CA0106 (Pulse Audio Mixer)

Open Volume Control and Device is set to CA0106 (ALSA mixer)

In Hydrogen, under Tools>Preferences>Audio System I set output to ALSA

These settings work for everything else with the keyboard.

---

