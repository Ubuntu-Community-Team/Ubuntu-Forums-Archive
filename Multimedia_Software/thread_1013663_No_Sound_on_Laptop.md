---
title: "No Sound on Laptop"
date: 2008-12-17
forum: Multimedia Software
---

### Post by deadlydes on 2008-12-17
Hiya
I have been using Ubuntu for a while now and love it.
I have just installed on my laptop but i cant get the sound to work, i have tried all the volume controls etc and googling but i cant get an answer.
The laptop is an Ergo Vista 201 (the sound works in wi*dows fine). I am running 8.10 (Intrepid)
Here is the info from lshw

 *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
 any ideas?

Thanks in advance

---

### Post by ajmorris on 2008-12-18
hi there,
that chip should work perfectly out of the box... try opening a terminal, and running:
```
sudo alsaconf
```

then use a mixer to test it out.


AJ

---

### Post by deadlydes on 2008-12-18
Hiya
Thanks for the reply
I ran that command and it couldnt find it so i googled and found a thread that suggested
sudo apt-get install alsa-base alsa-oss alsa-utils
sudo alsaconfig
reboot

I have tried that and then went to alsamixer via terminal and the master is upto full volume and there are no other channels. still not working

Strange its one of the supported chips.

did i do this right?
Thanks
Des

---

