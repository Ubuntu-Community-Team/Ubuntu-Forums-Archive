---
title: "PLEASE HELP! no sound through laptop speakers only headphones"
date: 2009-08-24
forum: Multimedia Software
---

### Post by page6159 on 2009-08-24
[B]Hi people,
I'm new to ubuntu and linux in general. I've just install 9.04 after getting pissed off with vista being sooooo slow. Basically I'm very impressed but not having any sound is driving me mad!!!! All the sound worked fine on vista but on ubuntu I am only getting any audio if I plug in some earphones, but that sucks I want my built in laptop speakers to work! I have tried all the simple stuff like checking they are not muted in the volumn control panel. when i open the volumn control panel I have 6 devices...
HDA ATI SB (alsa mixer)
HDA ATI HDMI (alsa mixer)
IDT 92HD71B7X (Oss mixer)
playback: HDA ATI SB - STAC92xx Analog (pulseaudio mixer)
capture: monitor of [/B]**HDA ATI SB - STAC92xx Analog (pulseaudio mixer)**
**capture: ****HDA ATI SB - STAC92xx Analog (pulseaudio mixer)**
All of them have the volumn turned up and are not muted.
If i open the sound preferences, all the settings are set to autodetect, i have tried going through them all but with no success.
I can also select preferences/default sound card and have 3 choices...SB, HDMI, and Pulseaudio, I have tried all three but no success.
Please help guys!

---

### Post by ygavesh on 2009-08-24
Try the following command and reboot, hope it will work.

The conditions where I tried this were the sound was horrible and I was using 8.10, my speakers were IDT so are yours. May be it will help, give it a try.

sudo echo "options snd-hda-intel enable_msi=1" >> /etc/modprobe.d/alsa-base

If you want to try a ready made ubuntu go to this blog and read on.
[www.gaveshedition.wordpress.com](www.gaveshedition.wordpress.com) :)

---

