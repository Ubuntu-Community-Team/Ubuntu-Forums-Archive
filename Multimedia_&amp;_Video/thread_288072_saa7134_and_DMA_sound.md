---
title: "saa7134 and DMA sound"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by clpc on 2006-10-29
I have spent 2 days now getting my Kworld xpert pvr plus v-stream TV card working but I still have a problem.
The sound is DMA and I do NOT want DMA sound, I want sound to come out the sound socket on the TV card. I assume (maybe wrongly) that you either get DMA sound direct off the PCI bus or you get sound from the TV cards output socket but not both.
The reasoning behind this is that if I watch a video on the Composite in then the only way I can get sound is to use the soundcard input for the sound and when I watch a TV channel I get DMA sound. If I connect the TV card sound output to the soundcard and the Composite audio to the TV card input then I will always get the sound through the soundcard no matter whether I am watching TV or composite video.

So here is my settings....
options saa7134 card=63 tuner=38  (this is according to the tuner & card lists for linux)
if I run this
sudo arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -
before running tvtime then I get audio via DMA.
if I don't then I get no audio and there is no audio coming out of the TV cards audio out socket. The DMA audio has a latency of a few hundred milliseconds so the lip-sync is slightly out, but its enough to ruin watching TV.

So the big question is.....
Does anyone out there know how I can get the audio to come out of the TV card itself? ](*,) 

I am running ubuntu 6.10 efty edge. Gnome desktop.
The card works fine the way I want it to in windows but I would rather not go back there.... in fact I wont go back there... the foot is coming down.... that's it the foot is down.

---

### Post by darkteckno on 2006-11-07
> **clpc said:**
> I have spent 2 days now getting my Kworld xpert pvr plus v-stream TV card working but I still have a problem.
The sound is DMA and I do NOT want DMA sound, I want sound to come out the sound socket on the TV card. I assume (maybe wrongly) that you either get DMA sound direct off the PCI bus or you get sound from the TV cards output socket but not both.
The reasoning behind this is that if I watch a video on the Composite in then the only way I can get sound is to use the soundcard input for the sound and when I watch a TV channel I get DMA sound. If I connect the TV card sound output to the soundcard and the Composite audio to the TV card input then I will always get the sound through the soundcard no matter whether I am watching TV or composite video.

So here is my settings....
options saa7134 card=63 tuner=38  (this is according to the tuner & card lists for linux)
if I run this
sudo arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -
before running tvtime then I get audio via DMA.
if I don't then I get no audio and there is no audio coming out of the TV cards audio out socket. The DMA audio has a latency of a few hundred milliseconds so the lip-sync is slightly out, but its enough to ruin watching TV.

So the big question is.....
Does anyone out there know how I can get the audio to come out of the TV card itself? ](*,) 

I am running ubuntu 6.10 efty edge. Gnome desktop.
The card works fine the way I want it to in windows but I would rather not go back there.... in fact I wont go back there... the foot is coming down.... that's it the foot is down.
May be worth asking here: [http://tech.groups.yahoo.com/group/KWORLD-TV/](http://tech.groups.yahoo.com/group/KWORLD-TV/)

---

