---
title: "No sound in ubuntu"
date: 2017-08-26
forum: Multimedia Software
---

### Post by eroloo on 2017-08-26
Hello, i have not sound in my ubuntu.
I installed my ubuntu today. I use integrated sound card.
Computer isnt notebook, i have not spekers in my computer.
I attach my **headphones.**

When i click audio icon in up-right corner in **'play sound through**' i see only option **digital output**


[I]Linux xxxxx 4.10.0-32-generic #36~16.04.1-Ubuntu SMP Wed Aug 9 09:19:02 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

[/I]In **alsamixer **everything is maximum, but i **can not change headphone value  **(ITEM = headphone[off,off])

when i use [B]pacmd list-sinks:

[/B]at index zero i have 
alsa.card_name = "HDA NVidia" **suspended** but **when i start** playing music it enters a** running** state. 

When i write (from offical troubleshooting)
[I]killall pulseaudio; rm -r ~/.config/pulse/* ; rm -r ~/.pulse*

[/I]it returns **rm: cannot remove '/home/xxxx/.pulse*': No such file or directory**when i enter a sound control pulseaudio program via gui in card output devices i have two devices
[I]built in analog stero/ port headphones (unplugged)
rv670/680 HDMI Audio/ port HDMI (unplugged)

installed 
sudo apt-get install ubuntu-restricted-extras
newest pulseaudio.

really need help, im tired out this problems.
thanks in advance. **if you need more information i will write it as soon as it possible**



[/I]

---

### Post by Yellow Pasque on 2017-08-26
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by eroloo on 2017-08-27
Thank you for fast reply.
Here is a link [http://www.alsa-project.org/db/?f=8c2653b78724e4a869a142b1069c7322514811d1](http://www.alsa-project.org/db/?f=8c2653b78724e4a869a142b1069c7322514811d1)

---

### Post by Yellow Pasque on 2017-08-27
Are you trying to use the front headphone jack or a rear one? Have you tried both?
What kind of system is this?

```
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
```
Are you sure you can't change this setting to 'on' in alsamixer? Have you tried using up and down arrow and/or 'm' key?

---

### Post by eroloo on 2017-08-28
I tried both jacks. Ubuntu 16.04
I can change off to on in alsamixer by 'm' key. Anyway arrows do nothing. Value is still 00 and i cant change it.
thats my alsamixer : 

[http://imgur.com/a/Xn3uM](http://imgur.com/a/Xn3uM)
i am worried about this 

[http://imgur.com/xCRTbV9](http://imgur.com/xCRTbV9)

it is ok that i cant see any devices? 
it is possible that my sound card is broken?

---

### Post by Yellow Pasque on 2017-08-28
> Value is still 00 and i cant change it.

It's the letter 'O', not the number '0'. So it's off or on. There is no volume number for the headphone control. I'm guessing the headphone volume is controlled with master and/or PCM volume levels.

> it is ok that i cant see any devices? 
No. There should be an analog option.

> it is possible that my sound card is broken? 
Possible, but very unlikely. It's more likely a problem with pulseaudio not recognizing analog output is available.

The best advice I can give:
1. Test your headphones on another device to make sure they work
2. Make sure Headphone output is on/enabled and reset pulseaudio:
```
rm -r ~/.config/pulse*; pulseaudio -k
```
3. If still having issues, file a bug report against pulseaudio

---

### Post by eroloo on 2017-08-29
I surrender. Just bought new USB sound card for 5 dollars. It works. :p thank you for your time. You are great man ; )

---

