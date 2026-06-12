---
title: "Limited Sound with HP DV7 1132nr Laptop x64"
date: 2009-07-25
forum: Multimedia Software
---

### Post by sammyboy405 on 2009-07-25
Ive Tried both Kubuntu and Ubuntu.  Both have the same issues with Audio. It basically plays when it wants too.  I Dont know how else to explain it. Im pretty savvy with *INUX until i get to messing with drivers and such.

I tried installing ALSA, that went over like a turd in a punch bowl.  I really screwed things up to the point where I just reloaded. 

So Im on a Fresh load of Kubuntu now.  I Have audio on some things and some I dont.

I have all the restricted packages loaded for mp3's and such.

Here is my sound info:

```
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
        Subsystem: ATI Technologies Inc RS780 Azalia controller   
        Flags: bus master, fast devsel, latency 0, IRQ 19         
        Memory at d2410000 (32-bit, non-prefetchable) [size=16K]  
        Capabilities: [50] Power Management version 3             
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-                                                                         
        Kernel driver in use: HDA Intel                                         
        Kernel modules: snd-hda-intel 

```

Any Help or Direction pointing would be appreciated.

---

### Post by sammyboy405 on 2009-07-27
So Since its says I Have
```
Audio device: ATI Technologies Inc RS780 Azalia controller
```

Is there another driver I need to use? Because it shows me using a Intel Driver?

---

### Post by sammyboy405 on 2009-07-28
.bump.. since its now nearing page 10 i dont think people work past page 5

---

### Post by igorzwx on 2009-07-29
Azalia may not work with OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

you can ask on OSS4 forum (they know everything about such things)

---

