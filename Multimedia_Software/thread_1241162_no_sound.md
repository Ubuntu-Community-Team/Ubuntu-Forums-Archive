---
title: "no sound"
date: 2009-08-15
forum: Multimedia Software
---

### Post by vp4cmb on 2009-08-15
I am a total newbie to Ubuntu, I installed it but have no sound.  Can someone give me step by step instructions to fix this problem?

---

### Post by joshjh on 2009-08-15
what kind of computer is it? If its a HP do what topcoder says here. i had the same problem. [http://ubuntuforums.org/showthread.php?t=1073090&highlight=pavilion&page=10](http://ubuntuforums.org/showthread.php?t=1073090&highlight=pavilion&page=10)

---

### Post by vp4cmb on 2009-08-15
Rebuilt ASUS M3A78 series motherboard

---

### Post by martinbaselier on 2009-08-15
Please paste the output of:

**sudo lshw -c multimedia**

---

### Post by vp4cmb on 2009-08-16
Here it is,*-multimedia            
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel
  *-multimedia
       description: Multimedia audio controller
       product: 5880B [AudioPCI]
       vendor: Ensoniq
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ENS1371 latency=64 maxlatency=128 mingnt=12 module=snd_ens1371
gregory@gregory-desktop:~$ 
Appreciate any help.

Thank you

---

