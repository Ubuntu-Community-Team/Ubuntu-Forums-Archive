---
title: "Latest kernell update messed up S/PDIF Audio(only DTS/AC3 works)"
date: 2008-08-28
forum: Multimedia Software
---

### Post by Zarok on 2008-08-28
I have an audio setup running that should direct ALL audio through S/PDIF out on my realtek integrated soundcard on a MSI P775 Platinum motherboard. I had it working in the previous kernel, but the update from yesterday messed something up.

I have unmuted IEC958 and I have AC3 / DTS audio working on SMplayer,VLC etc. Its just that every time I try any other audio like OS audio messages, avis with mp3 audio encoded etc, nothing works. 

SMPlayer and VLC are setup to use S/PDIF when available and use Alsa as audio driver, which is what worked previously. Now I only have audio on the DTS/AC3 material. 

So, what did the latest kernel update edit from my settings to mess this up, and how could I fix it? :/

Edit : I also tried upgrading Alsa to 1.0.1.7 using the script in the upgrade alsa-topic, it did upgrade it and I got a new IEC958-related switch calld IEC958 Default PCM which is also unmuted, still no audio on OS, browser, mp3 etc. Only DTS / AC3.

---

