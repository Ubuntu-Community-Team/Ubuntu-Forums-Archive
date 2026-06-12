---
title: "no sound"
date: 2008-12-09
forum: Multimedia Software
---

### Post by mastergoomba on 2008-12-09
this isn't the first time this has happened. what do i need to add to get sound? i have no clue what type of sound card i have, i just know it's onboard.

---

### Post by cariboo on 2008-12-09
If you open a Application-->Accessories-->Terminal and type:

```
sudo lshw -C sound
```

Paste the output of the above command in your next post. This will tells us what sound card you have, and we should be able to help you with your problem.

Jim

---

### Post by mastergoomba on 2008-12-09
guest@lilypad:~$ sudo lshw -C sound
sudo: can't set runas group vector: Operation not permitted
guest@lilypad:~$ 

that's what i got. nvm.....i figured it out

---

### Post by mastergoomba on 2008-12-09
okay, so, here's what i actually got when i put it in under the right account.

mastergoomba@lilypad:~$ sudo lshw -C sound
[sudo] password for mastergoomba: 
PCI (sysfs)  



  *-multimedia            
       description: Multimedia audio controller
       product: nForce2 AC97 Audio Controler (MCP)
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
  *-multimedia
       description: Multimedia audio controller
       product: SB Audigy
       vendor: Creative Labs
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=EMU10K1_Audigy latency=32 maxlatency=20 mingnt=2 module=snd_emu10k1

---

### Post by mastergoomba on 2008-12-15
bump

---

### Post by Flaffen on 2008-12-16
I'm a newb too, just wondering, have you gone to System -> Preferences -> Sound?
Cuz mine diddent work on autodetect, had to switch to Alsa or OSS.
(Alsa was laggy for me so chose OSS). Btw, that might also tell u what sound card u got.

---

### Post by mastergoomba on 2008-12-17
i know what kind of sound card i've got. and i'm not exactly a n00b, i've just never been able to solve this problem. 

how do you do the alsa/oss thing?

---

