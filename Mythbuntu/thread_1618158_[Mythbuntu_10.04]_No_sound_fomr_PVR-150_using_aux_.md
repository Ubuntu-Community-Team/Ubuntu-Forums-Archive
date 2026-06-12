---
title: "[Mythbuntu 10.04] No sound fomr PVR-150 using aux input"
date: 2010-11-10
forum: Mythbuntu
---

### Post by kyphos on 2010-11-10
I'm brand-new to Ubuntu and Mythbuntu.
My newly-installed Mythbuntu 10.04 system has a PVR-150 (configured at video0).
There are two physical media connections to it: one is coax from my analog cable service (tuner input).
The second is S-VID + stereo audio, fed from my digital settop box.
I defined two connections to the card: one for the tuner input, and one for the S-VID input.

If mythtv records a show using the tuner input, all is well. I get video and audio in the recorded file.
But if it records a show using the S-VID input, the audio is badly corrupted.  It's there, but very weak and badly distorted.

Similarly, if I watch LiveTV and choose channel 1 (which is defined as the S-VID source on the PVR-150), I get picture but no sound.

After hours of googling, I understand that the PVR-150 multiplexes the video and audio into the MPEG-2 digital stream.  Thus, the captured audio doesn't go through alsa.  Even so, I've fiddled with all the alsa capture sliders to no avail. 

I've used the PVR-150 with its S-VID interface on a Gentoo/MythTV system, and it works fine, so I know that the PVR-150 is capable of capturing the sound that accompanies S-VID input.  Where-oh-where are the buttons to push that adjust the audio settings for the PVR-150?

Thanks.

---

