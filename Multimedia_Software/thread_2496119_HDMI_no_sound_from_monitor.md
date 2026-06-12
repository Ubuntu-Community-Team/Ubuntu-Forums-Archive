---
title: "HDMI no sound from monitor"
date: 2024-03-14
forum: Multimedia Software
---

### Post by MadMonkey1966 on 2024-03-14
I recently noticed that the sound is no longer coming from my monitor built in speakers.
I  don't normally use the sound for music etc...anyway, so had not  noticed. Today I wanted to watch a live stream on YouTube, but no sound.  If I switch to the base unit built in, all is OK.

I have a Lenovo ThinkCentre running Ubuntu 22.04.4 LTS

Any help would be great.....

---

### Post by VMC on 2024-03-14
Check settings,sound,output device. There might be a couple of selections for HDMI.

---

### Post by MadMonkey1966 on 2024-03-17
HI VMC, thanks for the reply.......sorry for delay in getting back, I've been away.

Nope, I only have 2 output devices HDMI or built in speakers (if I switch to that I do get sound).

When I set it to HDMI, the little volume bar displays that there should be music, but nothing.... I have been into the monitor setting a done a factory reset as well...most perplexing

---

### Post by VMC on 2024-03-17
What's the output of this ```
lspci -v | grep -A7 -i "audio"
```

---

### Post by MadMonkey1966 on 2024-03-20
ok, output is...
>     Subsystem: Lenovo 7 Series/C216 Chipset Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f7c30000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])


---

### Post by VMC on 2024-03-20
"Capabilities: <access denied>" Try again using root. The Capabilities will be revealed.
Lenovo 7  might need a driver for it to work. 

Maybe someone with similar audio will respond.

---

### Post by MadMonkey1966 on 2024-03-21
So as root, i get...
> 00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Lenovo 7 Series/C216 Chipset Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f7c30000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link



---

