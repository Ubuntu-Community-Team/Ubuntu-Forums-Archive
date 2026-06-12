---
title: "Making my sound card work"
date: 2009-09-11
forum: Multimedia Software
---

### Post by Clove7 on 2009-09-11
>_< I've tried everything; followed all kinds of how-tos, from here, from google. I can't get anything to work at all. Here is some info:


[LIST]
[*]Alsamixer does work (indicating that the card should be working?)
[*]The card inside alsamixer says it's a HDA intel
[*]From LSPCI:
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Device 30b2                                                
        Flags: bus master, fast devsel, latency 0, IRQ 22                                             
        Memory at d4340000 (64-bit, non-prefetchable) [size=16K]                                      
        Capabilities: <access denied>                                                                 
        Kernel driver in use: HDA Intel                                                               
        Kernel modules: snd-hda-intel

```
[*]The laptop is an HP dv2000
[/LIST]

 
I just CAN'T get the audio to work :(. Halp please
 
Edit, and it's not muted :p.

---

### Post by Clove7 on 2009-09-11
I FINALLY got it to work :popcorn:. I right clicked my volume in the system tray, clicked select master channel and changed it to PCM-2. That worked :).

---

