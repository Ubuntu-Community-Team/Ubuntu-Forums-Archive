---
title: "weird sound problem (very noisy)"
date: 2008-06-13
forum: Multimedia Software
---

### Post by bigpimpatl on 2008-06-13
I have a weird sound problem. Anytime I play an mp3 in Amarok, BMPx, and JUK it sounds like my speakers are blown; very inflated, rough, and unnecessarily loud/noisy. but surprisingly this doesn't happen when i play an mp3 on totem movie player. I also have this same problem when watching flash video on firefox. I never had this problem before either. I reinstalled all the codecs for mp3 and still not working. I checked FLAC files and they are playing OK (on all programs). what is the problem? I have integrated audio, Realtek ALC850 codec, Compliance with AC97 v2.3 Spec.

running ubuntu 8.04 with kernel linux 2.6.24-17 generic

any help/suggestions would be very much appreciated

---

### Post by bigpimpatl on 2008-06-13
I also downloaded a couple of packages such as id3lib because i couldn't successfully change the ID3 tags of mp3 without destroying it...could this be behind it?

---

### Post by xc3RnbFO8P on 2008-06-13
Check in Synaptic Package Manager if you got (and install if you haven't)
kdebase-bin, kdebase-bin-kde3, kdelibs4c2a,
kdelibs-data, kipi-plugins

Restart the computer

---

### Post by Pjotr123 on 2008-06-13
Check the sliders in alsamixergui:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(number 2 )

---

### Post by bigpimpatl on 2008-06-13
@ Ringi

I had every package except for kipi plugin. I restarted and amarok and juk still have the same problem. however BMPx is playing back just fine. =)

@ Pjotr123

I will try your suggestion when I get home later tonight, thanks for the help!

---

### Post by bigpimpatl on 2008-06-16
well i tried messing with the mixer, but no dice. I also tried updating the alsa drivers to 1.0.1.6. and still it doesnt work. I also tried trying different sound devices (ALSA, pulseaudio, NVIDIA CK85, OSS) and nothing seems to work. I'll keep scouring the internet for solutions, but if anyone has a suggestion please let me know! thanks

---

### Post by buknoii on 2008-08-11
i have the same problem, and after some searching in google i landed on this page --> [http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

try installing alsamixergui. i install it on my notebook and it works great!

---

