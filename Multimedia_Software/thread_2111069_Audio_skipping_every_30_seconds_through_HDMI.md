---
title: "Audio skipping every 30 seconds through HDMI"
date: 2013-01-31
forum: Multimedia Software
---

### Post by aarongc on 2013-01-31
Hi all. I'm running Kubuntu 12.10 64 on an ASUS eeebox 1501. It runs an older NVIDA ion system. I recently got a surround sound system and have managed to get ubuntu to play audio via the HDMI out (took a while to figure out I had to unmute S/PDIF).

The problem is that when playing most audio files, the sound skips every 30 seconds (almost exactly, e.g. skips at 0:30, 1:29, 1:59). It sounds like it's being briefly disconnected and reconnected, and the lights indicating signal to speakers on the receiver flash off for less than a second.

This seems to happen whenever I'm playing 44khz audio. It does not seem to happen with 48khz audio, i.e. when playing a DVD or very high quality DTS audio files. It does not happen if I switch to analog stereo and use the headphones port.

I have tried vlc with the Pulse, ALSA, and Jack backends selected and it happens with all three.

The problem happens in Unity, KDE, and XBMC.

I posted my alsa info here: [http://www.alsa-project.org/db/?f=fd771ec2ca958dd55647d1d41b26bec071f3cd50](http://www.alsa-project.org/db/?f=fd771ec2ca958dd55647d1d41b26bec071f3cd50)

I have tried the pulseaudio tsched=0 fix, no luck with that.

Any ideas appreciated.

Thanks,
Aaron

---

### Post by aarongc on 2013-01-31
Fixed. Just had to install jockey-kde and use that to install / enable the latest NVIDIA drivers.

---

