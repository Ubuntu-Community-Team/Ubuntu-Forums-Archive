---
title: "Dolby Audio Driver for Ubuntu 14.04"
date: 2015-01-17
forum: Multimedia Software
---

### Post by penuel1310 on 2015-01-17
Hi everyone, I need High Definition audio drivers for ubuntu. I need drivers that will help me record HD audio in Audacity and also for HD audio output.

"lspci" detected the following hardware:

Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)

---

### Post by Rob Sayer on 2015-01-17
Many makers of sound cards use "High Definition" in the model name.  It's basically meaningless.  Purely a marketing term stolen from HD video.  Many people have these cards and then play almost nothing but mp3 files.  And mp3 is definitely not high definition.

This ain't windows.  It's not just about downloading drivers.  Does your audio card work?  What's the issue here?

What type if audio are you talking about?  If you want true high res audio that would mean more bit depth than CD, eg. 24/96 or 24/192.  Though I don't see the point of 24 bit audio ... it's been convincingly shown you can't actually tell the difference between redbook and 24/96 ... but others want it.

24 bit audio is a bit of a nest of worms in linux, as in audio generally.  It's the one thing in linux I don't find at all straightforward.  Try:

[http://thewelltemperedcomputer.com/Linux/Linux.htm](http://thewelltemperedcomputer.com/Linux/Linux.htm)

---

### Post by penuel1310 on 2015-01-17
Yes, my audio card works. I was looking for a way to improve the quality of the sound. 
Under windows, sounds seem 3d  ish... in other words, it feels like surrounded sound, but under Ubuntu sounds seem like 2d ish.. it's just so linear.
Any solution for that?

---

### Post by Yellow Pasque on 2015-01-17
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by penuel1310 on 2015-01-18
Here: Alsa information,

[http://www.alsa-project.org/db/?f=407615b888d2ac7f48ab816d90abeef79c31f13b](http://www.alsa-project.org/db/?f=407615b888d2ac7f48ab816d90abeef79c31f13b)

---

### Post by Yellow Pasque on 2015-01-18
You're not going to get any Dolby voodoo driver on Linux: [https://github.com/leoluk/thinkpad-stuff/wiki/Haswell-ThinkPad-problems#linux-low-audio-quality](https://github.com/leoluk/thinkpad-stuff/wiki/Haswell-ThinkPad-problems#linux-low-audio-quality)

---

### Post by jason-gotsch-gmail on 2015-09-28
> **penuel1310 said:**
> Yes, my audio card works. I was looking for a way to improve the quality of the sound.  Under windows, sounds seem 3d  ish... in other words, it feels like surrounded sound, but under Ubuntu sounds seem like 2d ish.. it's just so linear. Any solution for that?  Hello  penuel1310,
Actually, I understand what you mean. The "3D" you are hearing in windows is probably audio compression and processing by Windows and/or the Dolby (Sound Room?) software.  If I recall, the Dolby software also lets you move the EQ around to tweak the sound further. While some apps like VLC Media Player do provide sound compressor/spatializer/EQ capabilities -- like you I was looking for software to do this at the system level.  Unfortunately I haven't found a way to do this.  However, something you might check out is PulseAudio Multiband EQ.  It's no longer actively supported -- but many people including myself think it works pretty good and gives you some control over the "feel" of your sound output.  It doesn't provide compressor/spatializer capability -- but you can at least shape your sound a little better.  To install: 

sudo add-apt-repository ppa:alex-wv/pulseaudio-equalizer-ppa
sudo apt-get update
sudo apt-get install pulseaudio-equalizer

---

