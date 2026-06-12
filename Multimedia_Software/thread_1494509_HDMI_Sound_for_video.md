---
title: "HDMI Sound for video"
date: 2010-05-27
forum: Multimedia Software
---

### Post by matyd on 2010-05-27
I have succeeded in getting movies to play on my television via hdmi cord but the only flaw is to get the sound to transmit... Right now I have stumbled on a work around (If you want to even call it that!). I am able to play movies using vlc or dragon player and can play the sound of the movie with amarok. So if I can synchronize the two programs and run the sound and the movie at the exact same time it works great. Please help me out with this. I'm running Kubuntu 10.04, Acer Aspire 6930. Thanks,
Matt

---

### Post by v1ad on 2010-05-27
did you check if you have the hdmi sound in System > Preferences > sound
check the output tab and if you see it there select the hdmi as default.

---

### Post by matyd on 2010-05-27
I looked under the 'Systems' tab in the K menu and found nothing called 'Preferences'. I have, however, went into the system settings and set the HDMI sound driver deal to the first preferred spot in the video management deal (looks like a speaker). The sound isn't the problem, it plays fine when playing the sound in amarok. The last movie I played i had to use Amarok to play the sound and VLC to play the movie.

---

### Post by matyd on 2010-05-27
*bump*

---

### Post by matyd on 2010-05-28
Bump

---

### Post by matyd on 2010-05-31
[COLOR=#000000]solved the problem, had to reboot after i set the output module to ALSA and set ALSA device name to: HDA Intel: INTEL HDMI (hw:0,3) in vlc[/COLOR]

---

