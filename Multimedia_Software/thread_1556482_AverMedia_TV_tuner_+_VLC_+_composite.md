---
title: "AverMedia TV tuner + VLC + composite"
date: 2010-08-19
forum: Multimedia Software
---

### Post by erosoft on 2010-08-19
Hi all!

I have an AVerTV Hybrid Volar HX (a827) usb tv tuner card. Currently I'm able to watch everything with it (DVB-T, S-VIDEO/Composite,Analog TV). However recently I got set-top box for digital TV and started using the composite input. I was able to watch video with mplayer, but I want to get it to work with VLC. The last is because some of the channels are 16:9 and some are 4:3, and i have to restart mplayer to switch between aspect ratios. So how about VLC? Anyone able to use it with tv tuner and composite/s-video input?

p.s. this is the "script" I use with mplayer:
```
mplayer tv:// -tv driver=v4l2:device=/dev/video0:alsa:adevice=hw.1,0:amode=1:audiorate=48000:forceaudio:volume=100:immediatemode=0:normid=0:outfmt=YUY2:input=1 -aspect 16:9
```

---

