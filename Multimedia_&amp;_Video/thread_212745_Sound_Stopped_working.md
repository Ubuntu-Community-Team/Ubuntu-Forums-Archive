---
title: "Sound Stopped working"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by AdamBlack on 2006-07-10
New to linux and sound was working fine after installation of ubuntu. However, after a few days if finding and installing programs and what not it has suddenly stopped working.
I have been going through the comprehensive sound problem guide and this is my results:

aplay - l 
device_list:221: no soundcards found...

lspci -v
Finds my soundcard:
```
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=256]
        Memory at c6003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

```

I havn't been able to get onto the Alsa-Project website for days so I can't can't find the right driver.
I have tried a few of the ones that come up when usind sudo modprobe snd- but I get errors for all of them.
Any Suggestions?

---

### Post by AdamBlack on 2006-07-10
I put a SB Live 5.1 card in my comp to see if I could get that working. From What I could tell emu10K1 is the driver for it. I got through all the steps in the guide.
sudo modprobe snd- shows the emu10k1 driver
BUT
if i go sudo modprobe snd-emu10k1 it says

FATAL: Module snd_emu10k1 not found.
FATAL: Error running install command for snd_emu10k1

---

