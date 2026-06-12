---
title: "no volume control gstreamer plugins and or devices found"
date: 2009-07-03
forum: Multimedia Software
---

### Post by skarosg3 on 2009-07-03
Hi all.
I know that a lot of ppl had the same problem, and that alot of u have answered the same question but from what i have find on the internet, i just cant make this to work!

I have Ubuntu 8.10 and i was upgrading some things from the net yesterday, and since that i only had problems. just recently i managed to add me as an admin again(since i removed myself from that group) and now i am strugling to make the audio to work again!

I get this error
no volume control gstreamer plugins and or devices found
and no matter what i try, i still get no sound at all.
I tried to follow the post of LordRaiden, on the subject [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=205449&highlight=plugins+devices+volume+control+gstreamer+found](http://ubuntuforums.org/showthread.php?t=205449&highlight=plugins+devices+volume+control+gstreamer+found)[/COLOR]
but i cant figure out the driver for my sound card on the alsa site.
when i run lspci -v i get
```
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 006d
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        I/O ports at 1400 [size=256]
        I/O ports at 1c00 [size=128]
        Memory at e0002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
```
so i have a nVidia chipset, but i cant find the driver i need!

could u please help? thanks a lot!

---

