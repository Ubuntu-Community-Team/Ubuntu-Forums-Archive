---
title: "Absolutely No Sound"
date: 2011-03-18
forum: Multimedia Software
---

### Post by tsarprodigy on 2011-03-18
I have absolutely no sound. Nothing when i log in, nothing when something is plugged into the headphones jack, nothing at all.

i've tried adding things to alsa-base.conf in /ect/modprobe.d/

When i play something, such as a youtube video, or something in Rhythmbox, i don't get anything either... I've ran out of ideas. I'll keep trying things, and update if I get anything... Any ideas at all will help!

I've had this problem for several days. it came out of nowhere after logging in one day.


Edit: I fixed it...
After playing with a some settings in the Sound Preferences menu... I found out what it was.
Somehow, under the hardware tab, the profile for my Internal Audio device got changed to Digital Stereo Duplex ( IEC958 ), and I changed it to Analog Stereo Duplex, then went to the Output tab, and changed the device from "Simultaneous output to Internal Audio Analog Stereo" to Internal Audio Analog Stereo, and the connector from Analog Headphones to Analog Output. Now, both headphones, and my laptop's built in speakers work.

---

