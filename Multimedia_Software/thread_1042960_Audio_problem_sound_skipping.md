---
title: "Audio problem sound skipping"
date: 2009-01-18
forum: Multimedia Software
---

### Post by itsmeok on 2009-01-18
Hi I have an issue with my sound in Kubuntu with Linuxmce. With playback of movies or music (basically all sound playback) the sound skips every few seconds. I have seen a lot of post on this forum about it. I not so experienced in linux to see which one could apply to my case and I would like to get some help on finding the right issue. I will give some additional information that I have found out on my journey until now (2 weeks)

I will post any log or output if necessary.

I have an ASUS A7V8X with a realtek on board sound chip: 
Output of lspci -v | less
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: ASUSTeK Computer Inc. A7V8X Motherboard (Realtek ALC650 codec)
        Flags: medium devsel, IRQ 19
        I/O ports at e000 [size=256]
        Capabilities: <access denied>

I have not been able to find on the ALSA website that this chipset is supported. 

I am asking myself a lot of questions:
- Should I install additional drivers
- Could it be a problem with buffering

---

### Post by itsmeok on 2009-01-18
Additional info:

When I choose audio output oss the skipping stops. It is only on the alsa output.

---

