---
title: "TV-tuner audio cable question"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by virx on 2008-03-28
If my TV-tuner audio output is connected to sound card CD analog audio input, then is it normal that I can change TV sound from Master and CD Volume bars but not from TV-time? In TV-time volumebar moves but no changes in volume.

Another problem is with VLC since I want use it for TV recording, but no sound in VLC if I use /dev/dsp for audio device. In such cable setup I should use some other audio device?

Thank you for reading.

---

### Post by virx on 2008-04-11
Nobody has any idea how to get sound controlling in tvtime and sound in VLC?

While VLC user /dev/dsp audio device 
```
cat /dev/dsp 
cat: /dev/dsp: Device or resource busy
```But if VLC is not playing then 

```
cat /dev/dsp
``` 
shows some machine code.

---

### Post by warp99 on 2008-04-11
If you have an analog card and depending on the type of card you have, for instance a cx88 device, the sound will be on /dev/dsp1 because it's captured by /dev/dsp:

[http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29](http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_%28cx2388x%29)

---

### Post by virx on 2008-04-11
Thank you for reply.

I have ASUS Hybrid P7131 (SAA7134 chip) analog+digital card. Digital part works almost perfectly, but anaolg is the trouble one. How I got sound to analog is here:
[http://ubuntuforums.org/showthread.php?t=735551](http://ubuntuforums.org/showthread.php?t=735551)

I don't have /dev/dsp1 only dsp.

One more thing - In VLC I get noise instead sound.

---

### Post by virx on 2008-04-29
Meanwhile update to Hardy final. Now there is already in kernel module saa7134-alsa and also I have /dev/dsp1 device.

Solved 2 problems:
1) adjusting sound from tvtime: 
tvtime --mixer=/dev/dsp:cd
now tvtime audio bar moves and sound changes, same time in Volume Control CD audio bar moves also.
2) sound to VLC:
vlc v4l:/dev/video0:norm=pal:frequency=207250:size=720x576:adev=/dev/dsp1:samplerate=1

In VLC I get message to terminal:
[00000348] main audio output warning: PTS is out of range (212056), dropping buffer

I dont get it if samplerate is over 30000, but then I hear Mickey Mouse talk.

---

