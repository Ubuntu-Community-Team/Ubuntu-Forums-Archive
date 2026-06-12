---
title: "Digital audio output not working in Ubuntu 10.10"
date: 2011-02-18
forum: Multimedia Software
---

### Post by pocketman* on 2011-02-18
I have a HP slimline s3300f computer with onboard sound. Ubuntu is not recognizing it properly. I have looked everywhere for a fix with no luck.

The computer runs an AMD AthlonTM 64 X2 Dual-Core Processor 5000+, with a 
NVIDIA GeForce 6150SE nForce 430 Chipset. The sound is Realtek ALC888S Audio.

I need the coax digital out otherwise I will have to go back to Windows.

---

### Post by inobe on 2011-02-18
you just need to turn it on, go into your mixer settings and select IEC958 and make sure it's not muted.

> I need the coax digital out otherwise I will have to go back to Windows.

why did you state this, you don't want to go back or something? :lol:

it's not a problem if you did, use what works for you, btw welcome to the forums :P

---

### Post by pocketman* on 2011-02-18
I would if I could. that option does not show up.

I just tried a realtek driver update thru the terminal and now I have a black screen of death. No commands are working. UUUURRRGH

here is more info

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
    Subsystem: Hewlett-Packard Company Device 2a66
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
    Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel

after update aplay: device list:235: no sound card found...

---

