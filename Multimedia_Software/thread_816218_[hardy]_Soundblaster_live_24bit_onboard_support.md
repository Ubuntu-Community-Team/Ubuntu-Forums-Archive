---
title: "[hardy] Soundblaster live 24bit onboard support"
date: 2008-06-02
forum: Multimedia Software
---

### Post by Oktotorf on 2008-06-02
Hello, 

Since I started using Ubuntu two months ago I have been able to fix all little problems EXCEPT this one:
I have a K8N Platinum MSI motherboard with 7.1 Soundblaster 24 bit Live onboard sound. There's a 5.1 speakerset hooked on to the computer. In Ubuntu Hardy I only get sound from my two front speakers. I installed alsa mixer GUI but playing around with the switches doesn't help a thing. I also wonder if I need to install or change something to make sure I get sound through my 5 speakers also when I'm playing 2 channel sound (like mp3's). 
What else can I try to make it work? Is there anyone out there with the same configuration that does have surround sound?

Thx in advance

---

### Post by wolfen69 on 2008-06-02
first, go here and do this:[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

then:
```
gksudo gedit /etc/pulse/daemon.conf
```

Find and uncomment line: (remove "#")
default-sample-channels
and change value from 2 to the number of speakers you have. then save.

it may seem daunting to a newbie, but take your time, and 15 min later you'll be done.

---

### Post by Oktotorf on 2008-06-02
Thanks for the reply, I followed the steps on the other topic and did what u said. In the Pulse Audio Manager it keeps showing only 2 channels (front-left,front-right). 
I also don't know if this is the right soundcard he's detecting: 
ALSA PCM on front:0 (CA0106) via DMA ? or *alsa_output.pci_1102_7_sound_card_0_alsa_playback_0*

I'll read up on the other page some more cause maybe I need to change some settings, but in the manager itself it's a little complicated..


Edit: Apperently it was't uncommented (there was still a ';' ) 
 So now it works, I find that the front center is louder then all the rest but ok... I'll play around with the volumes a bit. 

So... Thanks!

---

