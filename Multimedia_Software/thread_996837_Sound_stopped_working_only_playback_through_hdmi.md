---
title: "Sound stopped working only playback through hdmi"
date: 2008-11-29
forum: Multimedia Software
---

### Post by Sauerpower on 2008-11-29
Hi,

I've got a strange problem. I've got a pavilion dv9055 laptop and tried to get sound to work through hdmi on my tv. I enabled digital output in the mixer by enabling iec958 output and unmute digital-1 playback.
 
The sound worked on my tv and my laptop at the same time. I didn't like the sound of my laptop speakers combined with my tv so I muted the master channel. Everything looked perfect at that moment, but when I unmuted the master channel the laptop speakers remained quiet (Headphones aren't working either). 
Since then I haven't got the sound back, only sound through hdmi seems to be working now.
I think I've tried everything now to get my sound back. I think I played with every mixer setting possible and spent hours searching the net.
I even tried rebooting with a livecd and still no sound. So it looks like a hardware problem but that looks very strange to me. 
To me it looks like it can only output digital signals and no analog signals any more. 

here's the output of aplay -l

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Can anyone help me with this problem? It's a bit frustrating :confused:

---

