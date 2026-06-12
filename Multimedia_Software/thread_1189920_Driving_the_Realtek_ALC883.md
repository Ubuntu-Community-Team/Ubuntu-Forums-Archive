---
title: "Driving the Realtek ALC883"
date: 2009-06-17
forum: Multimedia Software
---

### Post by mulluysavage on 2009-06-17
Can you help me get the coax optical out working on my system?

Asus M3N78 pro (audio= Realtek ALC883)

I had the analog out working for  months, then got a new receiver with digital optical. Read a few posts, and saw that the IEC958 was muted by default. unmuted in Alsamixer, no luck. 

Then saw that you have to do a funky workaround to get this chip to work:
[http://www.mythtv.org/wiki/Intel_HD_Audio_-_Realtek_ALC88x](http://www.mythtv.org/wiki/Intel_HD_Audio_-_Realtek_ALC88x)
Involving muting, playing a sound, then unmuting:

amixer set IEC958 mute
aplay -D spdif /usr/share/sounds/alsa/Front_Center.wav
amixer set IEC958 unmute

I did this, then played the same sound, and I heard it, loud and clear!
Then I opened Songbird and got no sound. I went back and tried to play the sound again through the command line, and got no sound. Restarted, tried everything again... now no sound even through the analog output.

I also noticed that my modules are:
0_snd_hda_intel

And my ALC883 device 0 is analog and ALC883 device 1 is digital. Does this mean I need to load a snd_hda_intel driver at device 1 somehow?

Right now I have zero sound. :(

---

