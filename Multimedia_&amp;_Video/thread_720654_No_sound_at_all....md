---
title: "No sound at all..."
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by Pindulet on 2008-03-10
I've just installed gutsy on a fujitsu-siemens Amilo pro v2000 and everything seems to be working fine, but i have no sound. I looks like it recognises an audio driver but I hear no sound.

Here is the lshw output for the audio device, can anyone tell me what driver i have to install to get it to work. Or is it just me being stupid and not seeing thats it has been muted somewhere??

```
*-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
```

thanks in advance
Kristian

---

### Post by linuxwizard on 2008-03-12
Look through this

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by superprash2003 on 2008-03-12
hope this helps [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

