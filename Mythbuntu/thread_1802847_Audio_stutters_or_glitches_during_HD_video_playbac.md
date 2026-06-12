---
title: "Audio stutters or glitches during HD video playback"
date: 2011-07-12
forum: Mythbuntu
---

### Post by yonkiman on 2011-07-12
For years the audio on my MythTV has occasionally stuttered during playback, particularly of HD video.  I bought a new soundcard, a new motherboard, and kept upgrading MythTV (Mythbuntu), Ubuntu and the Alsa drivers to their latest release - sometimes the problem would get more or less frequent, but it never went away.  

Last week I wondered if there was any constant in all of this, and there was: my Nvidia 8400GS graphics card.  I'd read that the card was plenty fast for HD playback and the video always looked fine, so I hadn't thought it could be the problem.  But I thought I'd buy a faster card just in case - it was the only thing I hadn't tried.  I need component video output, so I bought an Nvidia 9500GT.

Problem solved!  Apparently the 8400GS, while it looked fine, was occasionally dropping a frame, and the audio would then glitch to stay in sync with the video.  Been watching all sorts of HD material with the 9500GT without a single glitch.

Hope this helps someone!

-Fred

---

