---
title: "Removed Pulseaudio and now I have NoAudio"
date: 2011-04-07
forum: Multimedia Software
---

### Post by GTMoraes on 2011-04-07
Hello, This problem is related to the Media Center PC (Check the config on my improvised sig.)

So, after following some instructions regarding how to remove the Pulseaudio, now I have no audio at all. Running the gstreamer-properties (both SUDO'ed or not) gives me positive results (With ALSA selected and HDMI Out), but I cannot hear system audio, musics, youtube, etc etc

BUT, for some reason, XBMC works a-OK. So does Audacious with some alternative configuration. Both doesn't obey the system volume settings. The others applications seems to be playing to nowhere.

I think I messed everything up by following two sites instead of only one. Something must be in conflict or missing.
I've followed **_[this site]("http://www.jeffsplace.net/node/12")_** and **_[this one]("http://jechem.blogspot.com/2010/10/how-to-remove-pulseaudio-on-ubuntu-1010.html")_**

Please help me, Sometimes I need to play a game or watch a video outside Youtube (XMBC plays youtube) and I have no sound.

Thank you =)

---
That's the sound config on Audacious:
Output Plugin: ALSA Output Plugin
PCM Device: plughw:CARD=HDMI,DEV=3 (HDA ATI HDMI, ATI HDMI Hardware device with all software conversions) [There are plenty of options, but that's the only one that work without giving me "snd_pcm_hw_params_set_format failed"]
Mixer Device: hw:0 (HDA ATI SB) [There's also "Default", that does nothing, and hw:1 (HDA ATI HDMI), that gives me 'Alsa Error: no suitable mixer element found']
Mixer Element: PCM
"Work around drain hangup" checked.
24bits output and "Use software volume control" checked.

---

P.S.: A/V is connected thru HDMI.
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 256MB | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" 1366x768 LED | 6:30hrs Battery
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by wolfen69 on 2011-04-07
See [this]("http://www.jeffsplace.net/node/12").

---

### Post by GTMoraes on 2011-04-07
Thanks for the reply.

I've followed this instruction.
> I think I messed everything up by following two sites instead of only one. Something must be in conflict or missing.
I've followed this site and this one

"This site" and "This one" are links. Sorry if it isn't very clear, I'll fix it up
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 256MB | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" 1366x768 LED | 6:30hrs Battery
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by GTMoraes on 2011-04-08
Nothing?
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 256MB | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" 1366x768 LED | 6:30hrs Battery
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by GTMoraes on 2011-04-09
Oh c'mon, there must be a way to fix this!!
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 256MB | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" 1366x768 LED | 6:30hrs Battery
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by lidex on 2011-04-10
Sounds similar to this:
[http://ubuntuforums.org/showthread.php?t=1717811](http://ubuntuforums.org/showthread.php?t=1717811)

---

### Post by GTMoraes on 2011-04-10
But I'm not using PulseAudio. Issue started when I removed it, actually.
With PulseAudio installed, I might recover the system audio, but [it'll keep crashing the system during video playback]("http://forum.xbmc.org/showthread.php?p=766051#post766051")
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 256MB | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" 1366x768 LED | 6:30hrs Battery
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by Yellow Pasque on 2011-04-10
It sounds like you just need to set programs to using ALSA (this is different for every app). Either that or reinstall pulse and use pasuspender when you run xbmc.

---

### Post by GTMoraes on 2011-04-10
PASuspender? I'll take a look at it when I'm at home. Thanks =)
Hm.. There are hundreds of millions tutorials regarding how to remove PulseAudio... But none to reinstall it.

Can someone lead me to the right place? Thanks!

[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 256MB | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" 1366x768 LED | 6:30hrs Battery
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

