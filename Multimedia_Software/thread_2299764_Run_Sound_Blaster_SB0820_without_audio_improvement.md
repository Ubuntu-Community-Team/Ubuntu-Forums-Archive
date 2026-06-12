---
title: "Run Sound Blaster SB0820 without audio improvements"
date: 2015-10-21
forum: Multimedia Software
---

### Post by Roland_Rieger on 2015-10-21
Dear Folks,

the card is working very well at the moement by using the analog jack. 
The analog jack is used in case of the great DAC on the card.

The only issue is that I have got is the bad feeling there are running some audio improvements that are for normally can be disabled in MS-Style OS.
In a MS-OS the feauture in the driver software is called "Crystalizer". This feauture would be great to be disabled - i would like to hear the music like it is recorded on the 
studio.

Attached you will find my configuration of **/etc/pulse/deamon.conf**

Cheers
Roland


3.13.0-24-generic

07:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
08:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

---

### Post by Yellow Pasque on 2015-10-21
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

EDIT: Or you can look at the available options in alsamixer which is why I asked for the info. Remember that space bar toggles options and you may have to hit the right arrow repeatedly to see options not shown on the initial screen.
```
alsamixer
```

---

### Post by Rob Sayer on 2015-10-24
I've read a bunch of forum threads about Creative Labs in ubuntu.  AFAIK the options like the 'crystallizer' (which is just frakking EQ BTW) don't work in Linux.  This isn't unheard of in linux and sounds like about what you want.  So would I.

I had a look at your pulse config file and on my setup I'd change the 48000 default sample rate to 44100.  I have no interest in high res audio ... the only advantage is that the mastering is often better ... and I don't really care if the audio in videos is resampled.  All my music is 44.1K Redbook based or downsampled to that.  I also change the dmix sample rate default in the alsa config file.

---

