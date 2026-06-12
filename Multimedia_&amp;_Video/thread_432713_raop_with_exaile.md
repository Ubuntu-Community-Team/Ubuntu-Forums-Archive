---
title: "raop with exaile"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by dswebb on 2007-05-04
Hi All,

I am using exaile now and would like to get it working with raop ([http://raop-play.sourceforge.net/](http://raop-play.sourceforge.net/)) in order to stream to my airport express.  Unfortunately exaile doens't seem to be able to configure which alsa device that it can use.  Has anyone been able to get Exaile working with raop?  

I am on Edgy 6.10 and am using the latest version of raop.  

Or does any one know of another means of streaming to an airport express from exaile?

Cheers,

Danny

---

### Post by dannyswebb on 2007-05-15
If anyone was interested on how to get exaile working with RAOP.  

All I had to do was change the default ALSA soundcard to the raop pcm device.

First task is to find out what card and device it is assigned to.  This is done by using aplay -l

foo@foo:~/$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: raoppcm [ALSA RAOPPCM], device 0: raop pcm [raop pcm]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


In this instance my RAOP driver is loaded as card 2, device 0

So, in my ~/.asoundrc file I setup:


pcm.!default {
            type hw
        card 2
        device 0
}

ctl.!default {
    type hw
    card 2
}

This makes the RAOP device the default device for ALSA and exaile will pick it up.

:guitar:

---

