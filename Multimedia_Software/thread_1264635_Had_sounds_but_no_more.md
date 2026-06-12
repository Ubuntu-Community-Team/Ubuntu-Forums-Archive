---
title: "Had sounds but no more"
date: 2009-09-12
forum: Multimedia Software
---

### Post by Sambie on 2009-09-12
I'm having some difficulties of trying to get my sounds to work. It was working perfectly before. My sound card is attached to the motherboard. What are the options for checking to see if my sound card is working or not without having to load windows on another partition?

what do I need to put in to get my sounds to work again?

---

### Post by Sambie on 2009-09-12
bump

---

### Post by HappyFeet on 2009-09-12
Did you check your volume controls? (not the little speaker icon)

---

### Post by Sambie on 2009-09-13
The volume controls are normal.

My power supply died some time ago and just recently I got a new one. I turned on my computer and the sounds were normal but my computer crashed. I went to turn on my computer again and from then on I received no sounds.

---

### Post by Sambie on 2009-09-13
Ok I'm trying to remember clearly of what exactly happen and I can remember when I first logged on my computer after I installed my new Power supply. I wasn't able to use my computer during the time so I wasn't able to download the updates. Before I've updated Ubuntu the sounds were running perfectly without a problem but it seems like right after I updated Ubuntu the sounds seems to have diminished.

I went to terminal and used this code: aplay -l

This is what I got back so I know my soundbard from my motherboard is being seen.

[B]**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]

After using this code: lspci -v | less to check if my sound card is physically installed and recognized by my hardware.

I've received this:

[B]80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
        Subsystem: ASRock Incorporation Device 0888
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f7efc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel[/B]

So I know my sound card is being seen but the question is how can I get Ubuntu to enable my sound card? I assume something happen during the updates.

---

### Post by Sambie on 2009-09-15
Problem fixed :D

Anyone having the same issues as I did you may want to go to [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and follow each steps.

---

