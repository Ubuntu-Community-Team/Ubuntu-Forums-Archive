---
title: "Satellite L305D internal mic not working"
date: 2011-04-01
forum: Multimedia Software
---

### Post by getmeoutofhere on 2011-04-01
My Toshiba Satellite L305D is running Ubuntu 10.10.  The internal microphone doesn't work - if I try to record something, I just hear some clicks.

According to the terminal, my audio device is:

ATI Technologies Inc SBx00 Azalia (Intel HDA)

When I click open alsamixer, the boxes for Front Mic, Mic Boost and Beep are empty.

When I go to Preferences => Sound => Hardware I get a choice of Analogue Stereo input, output and duplex - as well as off.  I go for duplex.  

When I go to sound => input, the microphone mute box in unchecked and the single volume bar is at a maximum.  There are no choices - the one choice, Internal Audio Analog Stereo, is checked.  As it's only once choice, it can't be unchecked.

Any ideas?  Thanks.

Any ideas on how to get the microphone to work?  Thanks.

---

### Post by getmeoutofhere on 2011-04-04
Any ideas?  I don't know where to start.  Thanks.

---

### Post by lidex on 2011-04-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by ashickur.noor on 2011-04-05
Don't tell any thing about Toshiba for Ubuntu. I am facing a lot of trouble to run 10.04 64 bit in L650D. In general I think Toshiba is one of the laptop manufacture which has the worst open source support.

---

### Post by getmeoutofhere on 2011-04-06
lidex,

Thanks for the reply.  The link is as follows:

[http://www.alsa-project.org/db/?f=15bc43a8e5c69dc164c14219418c35f47d5216b7](http://www.alsa-project.org/db/?f=15bc43a8e5c69dc164c14219418c35f47d5216b7)

---

### Post by lidex on 2011-04-06
OK, first of all you have added model quirk to alsa-base.conf that is not for your hardware. You need to remove that. Reboot and post this output:
```
amixer
```

---

### Post by getmeoutofhere on 2011-04-23
Thanks.  By the way it's just the internal microphone that's not working - when I plug a microphone into the microphone jack, that doesn't work either.  I made the change and here's the output:

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 2
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 12
  Mono:
  Front Left: Playback 0 [0%] [-24.00dB] [off]
  Front Right: Playback 0 [0%] [-24.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]

---

### Post by lidex on 2011-04-24
Please use code tags when posting text blocks. Try changing the values for 'mic boost' using alsamixer:
```
Simple mixer control 'Front Mic Boost',0
Capabilities: volume penum
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: 0 - 2
Front Left: 0 [0%]
Front Right: 0 [0%]
Simple mixer control 'Mic Boost',0
Capabilities: volume penum
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: 0 - 2
Front Left: 0 [0%]
Front Right: 0 [0%]
```

---

### Post by getmeoutofhere on 2011-04-24
Thanks.  How do I make the changes?  You mean add them to the alsa-base.conf file?

Might I have better luck waiting a few days and replacing the system with 11.04?  It seems a lot of people are having microphone problems with 10.10, and maybe this is a problem unique to this version.

---

### Post by getmeoutofhere on 2011-04-24
Sorry, I managed to changed the levels on alsamixer.  I can record something, but the distortion/interference is absolutely massive.

---

### Post by lidex on 2011-04-24
> **getmeoutofhere said:**
> Sorry, I managed to changed the levels on alsamixer.  I can record something, but the distortion/interference is absolutely massive.

Possibly having capture levels maxxed out as well as mic boost is creating distortion. Try backing down the capture levels.

---

