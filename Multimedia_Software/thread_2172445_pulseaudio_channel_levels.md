---
title: "pulseaudio channel levels"
date: 2013-09-05
forum: Multimedia Software
---

### Post by alex68 on 2013-09-05
So I've downloaded the kernel modules for ALSA to support my particular soundcard - one of the RME HDSP models. Standalone with alsaconf, alsamixer, and hdspmixer, sound works perfectly fine. The problem is some applications (like Skype) don't work because my soundcard is not listed under Sound in my control panel. Alas, I gave in and installed PulseAudio again. After a few hours of wrestling with PulseAudio, I was able to get it to recognize my soundcard and work with Skype. Now the problem is that for my headphones (I wasn't able to verify if this happens for my speakers because it was getting late and I didn't want to wake up my neighbors), the left channel is consistently louder than the right channel - even when listening to mono audio. I've verified this by eyeballing HDSPMixer - which shows the output level for each channel. When I disable PulseAudio, the levels are pretty much equal (create a flat level when a song is playing), but when I turn PulseAudio on, it is tilted down towards the right channel. I get the flatness in Windows 7, so I feel as if this problem is particular to PulseAudio. If it makes any difference, PulseAudio also makes the sound much louder and I need to lower the volumes when switching. I thought it might be some sort of balance shifting occurring from a drastic volume change from ALSA to PulseAudio (kind of like what happens when using attenuators, but only digitally with algorithms). I raised the volume for each channel so it was near -12.0db and the left channel was still consistently producing higher output. I'm not sure what to do.

---

### Post by CatKiller on 2013-09-05
It sounds to me like Pulse is mapping another channel (centre, maybe?) to the left side as well as the left channel. There is a speaker map option in Pulse's config files but I've no experience of how it works.

---

