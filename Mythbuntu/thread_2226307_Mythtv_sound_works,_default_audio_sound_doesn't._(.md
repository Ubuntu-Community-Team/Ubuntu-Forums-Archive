---
title: "Mythtv sound works, default audio sound doesn't. (Mythbuntu 14.04)"
date: 2014-05-26
forum: Mythbuntu
---

### Post by DeweyOxberger on 2014-05-26
Pardon me... another note to my future self.

You've installed Mythtv, in Myth you set the audio device and it works great but the default audio doesn't work (no sound in Chromium for example - no youtube sound; oh the horror).

In 2014 it looks like pulseaudio rules the default sound device and no amount of alsa asound.conf magic can help.

The fix: sudo apt-get install pavucontrol

Then tinker in pavucontrol.  I had to launch it several times, tinker a bit, and shut it down but eventually the configuration tab showed the device "High Definition Audio Controller".  The profile pick box on that tab had the entry for my TV (of the 10 or so entries on that pick box they all showed "unplugged" except one, and that one works).

So, go to Configuration, under "High Definition Audio Controller" set the pick box to the TV's "Digital Stereo (HDMI) Output".

Then go to Output Devices, find "High Definition Audio Controller" and activate the "Set as fallback" button (green circle with a check)  ("fallback == default maybe?)

I believe I then did a: pulseaudio --kill and a pulseaudio --start and the the default sound was being sent to the TV.

Audio fixed

---

