---
title: "Upgrade to 12.04 broke AC3 5.1 sound, but not AC3 stereo"
date: 2012-04-29
forum: Mythbuntu
---

### Post by AKADAP on 2012-04-29
Upgrade to 12.04 broke AC3 5.1 sound, but not AC3 stereo.

Old recordings & live TV that use AC3 5.1 sound are silent. If I select a different audio channel in AC3 stereo, or a TV channel using AC3 stereo, the sound is fine.

Sound was working fine before upgrading. (Before anyone says I should not have upgraded because it was working fine, the computer was not booting reliably in 11.10, so far I have not had a boot failure in 12.04, so even with this problem, it is an improvement)

---

### Post by nickrout on 2012-04-29
> **AKADAP said:**
> Upgrade to 12.04 broke AC3 5.1 sound, but not AC3 stereo.

Old recordings & live TV that use AC3 5.1 sound are silent. If I select a different audio channel in AC3 stereo, or a TV channel using AC3 stereo, the sound is fine.

Sound was working fine before upgrading. (Before anyone says I should not have upgraded because it was working fine, the computer was not booting reliably in 11.10, so far I have not had a boot failure in 12.04, so even with this problem, it is an improvement)

Was it the upgrade to 12.04 or the upgrade to 0.25? 
What are your audio settings?

---

### Post by AKADAP on 2012-04-29
> **nickrout said:**
> Was it the upgrade to 12.04 or the upgrade to 0.25? 
What are your audio settings?

It was the upgrade to 12.04. I have been running 0.25 from the daily builds for more than six months.

Audio settings:
Audio output device: ALSA:surround71:card=Intel,DEV=0
Speaker Configuration: 7.1
Upconvernt stereo to 5.1 surround: not set
Upmix quality: Best
Advanced settings:
Nothing checked except "HBR passthrough support"

Audio test will correctly send sound to the 7 speakers I have (I do not have a subwoffer, and there is no way to route the subwoffer channel to the 6 full range speakers I have.) I'm using an analog connection since I'm using a dual link DVI connection to my monitor and my reciever only supports HDMI or analog for more than 5.1 channels. Also my video card will only output 5.1 through HDMI, but won't output anything on HDMI unless it also outputs video to HDMI. Also SPDIF pass through was rather unreliable.

---

### Post by AKADAP on 2012-04-29
A bit more info:

I found a test AC3 5.1 file and it played fine in a different application.

On a hunch I changed the audio output device to Alsa:Pulse, and this appears to be working.

I am getting sound out of all 7 speakers, but I don't know what kind of decoding it is doing to get there.

---

