---
title: "What is the best native way to play soundfonts as an instrument?"
date: 2010-06-21
forum: Multimedia Software
---

### Post by delsydebothom on 2010-06-21
I am a composer with no money whose old music computer and keyboard were destroyed in an accident. I can't afford to replace them. However, I still have 320+ gb of soundfonts that I would like to play on my 64-bit Ubuntu 10.04 machine. No composing now; I just want to play them on my computer keyboard. The trouble is, I can't find any native Linux app that works. 

I used wine install the demo version of FL Studio 9, and I can play my soundfonts with it, but the latency is terrible. I have to set the latency to 65 milliseconds before I get anything but a stuttering mess. 

I'd really like to use Virtual MIDI Piano Keyboard, but the sound doesn't work, and I'm not sure how to troubleshoot it. The System Testing detects my sound device as "DA-Intel - HDA NVidia HDA NVidia at 0xfe024000 irq 21"

This makes no sense to me; since when does NVidia manufacture sound equipment? Is this a motherboard with integrated sound? Anyway, I would be immensely grateful for any help!

---

### Post by cbrunhaver on 2010-06-21
You might try this app:

[http://www.linuxsampler.org/](http://www.linuxsampler.org/)

I don't have experience with it but I believe that running ubuntu studio (which has a realtime kernel for lower latency etc.).  

Here is a bit of into on disabling pulseaudio in ubuntu studio.
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

BTW, I don't really know much about this stuff but wanted to try to help anyway.

---

