---
title: "Voume Control"
date: 2008-05-11
forum: Mythbuntu
---

### Post by Dragonflyoh on 2008-05-11
I have Mythbuntu 8.04 and am using the internal player for movies. When I use the volume control on the remote for movie or recording playback I get a pop up window that displays the volume control and indicates the volume is going up or down however the volume does not change. I have tried all sort of combinations on the sound set up page and nothing has worked. I am using the SPDIF output from my motherboard and sending the sound to my sound system. I changed the set up to use xine and the volume control worked however I was only able to get 2 channel stereo, no surround sound from xine. Any ideas would be appreciated.

---

### Post by ctucker10 on 2008-05-11
> **Dragonflyoh said:**
> I have Mythbuntu 8.04 and am using the internal player for movies. When I use the volume control on the remote for movie or recording playback I get a pop up window that displays the volume control and indicates the volume is going up or down however the volume does not change. I have tried all sort of combinations on the sound set up page and nothing has worked. I am using the SPDIF output from my motherboard and sending the sound to my sound system. I changed the set up to use xine and the volume control worked however I was only able to get 2 channel stereo, no surround sound from xine. Any ideas would be appreciated.

I had the same problem you describe. On the audio settings page, Utilities/Setup=>Setup=>General, I changed the Audio output device to /dev/dsp. I left all other settings at their default values. After that I logged out and back in again. That fixed it for me. I hope it works for you too.

---

### Post by Dragonflyoh on 2008-05-12
Thank you. I tried the change and lost all audio. I do not remember what the default settings were. My settings on the set up page are:
Mixer - PCM
Mixer device - ALSA:default
checked - use internal vol controls
checked - enable AC3 to SPDIF pass through
checked - enable DTS to SPDIF pass through
UPMIX - Active Linear
Max Audio Channels - Stereo
Passthrough output device - ALSA:Iec958 {AESO 0x02}
Audio Output Device - ALS:SPDIF
See anything that would be causing the problem?

---

### Post by parc on 2008-05-13
> **ctucker10 said:**
> I had the same problem you describe. On the audio settings page, Utilities/Setup=>Setup=>General, I changed the Audio output device to /dev/dsp. I left all other settings at their default values. After that I logged out and back in again. That fixed it for me. I hope it works for you too.

I had the same problem and this worked for me ! Thanks !

parc

---

