---
title: "SPDIF Sound stopped working"
date: 2010-02-21
forum: Multimedia Software
---

### Post by uhrenmacher on 2010-02-21
Hi there,
I installed Ubuntu 9.10. I switched the audio output to "Digital Stereo Output +  analog Stereo Input" and everything worked fine for some days on my digital 5.1 system (rhythmbox for example)

Now, after i installed VLCplayer and tried to watch a movie, there was no sound. - and now, all the system's sound is dead! (perhaps is was even broken before i installed vlc, im not sure)

What can i do ? I checked the Mute-option in the upper right corner, i checked all mute-options on console "alsamixer" - i removed and reinstalled pulseaudio, i wrote some alsa-config files (and removed them again).

On one point, "speaker-test -Dplug:iec958" gave me some sound, but rhythmbox did not. So i reinstalled pulseaudio again but now everything is dead again including system sound.

Any Ideas 4 me? thank you very much !!

---

### Post by ajgreeny on 2010-02-21
Install **padevchooser** if you have not already got it on the machine; it is not installed as default, for some reason, and I found it was needed, even though I did not actually change anything when I installed it.

Weird I know, but that seems to be pulseaudio at the moment; when it works it is very good,  but when it doesn't it's a real problem sorting it out.

---

