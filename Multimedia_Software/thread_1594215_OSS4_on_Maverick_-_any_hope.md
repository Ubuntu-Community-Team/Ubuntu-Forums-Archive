---
title: "OSS4 on Maverick - any hope?"
date: 2010-10-12
forum: Multimedia Software
---

### Post by stimuli on 2010-10-12
I'm on a Geode LX 500mhz laptop. As you might imagine, this machine is lacking in processing power. ALSA on the Geode LX/CS5536 chipset is abysmal... stuttering audio at best, and 100% CPU usage are all I can get. Throw in Pulseaudio for more of the same.

I've found OSS4 allows me to listen to MP3s and MPlayer movies, and leaves plenty of CPU to boot (albeit only 1 audio stream at a time, which is fine).

OSS4 worked great under 2.6.32 kernels, but Maverick Meerkat aka Ubuntu 10.10 ships with the much better 2.6.35 kernel. I've yet to get a working OSS4 setup, with either the broken-hasn't-worked-ever-why-is-it-in-the-repositories Ubuntu repository OSS4 packages, nor the worked-before .deb from 4front's opensound.com site.

It builds and installs fine, but doesn't start up correctly. No audio and warnings of no mixer.

Any ideas? I suspect I will have to wait for 4front to release a working .deb

ossinfo reports:
```
Version info: OSS 4.2 (b 2003/201007311944) (0x00040100) GPL
Platform: Linux/i586 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 (kjsa)

Number of audio devices:        0
Number of audio engines:        0
Number of MIDI devices:         0
Number of mixer devices:        0


Device objects
 0: osscore0 OSS core services
 1: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices

Audio devices

Nodes

```

lsmod | grep oss reports:
```
oss_usb                92545  0 
oss_geode               8451  0 
osscore               541033  2 oss_usb,oss_geode
```

---

### Post by hawks-SOAD on 2010-10-12
actually yes there is a hope im am running oss4 right now in maverick meercat :D

[http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html](http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html)

follow that , what i did is install all the oss4 packages in synaptic package manager , removed pulseaudio and black listed the alsa modules , i also configured gstreamer to use oss 4 , good luck its all in that article

---

### Post by stimuli on 2010-10-12
I tried your suggestion and same results :(

It appears to be a kernel level bug with geode CS5536 hardware(?)

---

### Post by stimuli on 2010-10-14
Solved. I grabbed the latest sources from Opensound.com's mercurial repository, deleted the ./contributions/ folder (ossmeter would break the make build), and built a working .deb. Since I built it myself I even have sound mixing now (by default vmix uses floating point mixing, which does not work on Geode LX).

Sound now works very well. 2.6.36 kernels, in particular, will need to use the updated sources, as the old busted sources in the repository won't even build.

---

