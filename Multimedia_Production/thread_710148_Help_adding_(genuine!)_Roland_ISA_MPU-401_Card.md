---
title: "Help adding (genuine!) Roland ISA MPU-401 Card"
date: 2008-02-28
forum: Multimedia Production
---

### Post by cthk26 on 2008-02-28
Hoping some forgiving guru will aid an Ubuntu noob...] 2 weeks of googling & reading man pages have only confused me too much.

I trying to get a Roland MPU-IPC-T ISA MIDI port to operate beside a SB Live Value PCI card. I have 2 MIDI KBs and numerous MIDI sound modules I'd like to run hence the need for a few more MIDI ports than usual.

I know the port (0x330) and IRQ (7) of the MPU-IPC card (that's all there is for this baby!). Where do I put them to get ALSA to find the card? 

The SB card is working fine, including analog audio, MIDI etc, I just can't seem to make the mental link as to where the ISA parameters need to go...

Running Ubuntu Studio 7.10.

TIA

Chris.

---

### Post by gomadtroll on 2008-02-28
ISA card, good luck :-) I am pretty sure that Ubuntu has comleteley and unequivicably deprecated the ISA slot and the tools that helped configure one. That said, if 'alsaconf' (CLI) is available I have had success configuring an ISA sound card. The down side is I could not get the configuration to stick through a reboot cycle. 

greg

---

### Post by cthk26 on 2008-02-28
Thanks for the advice.

I'll try alsaconf (I'm not at the machine right now) & report back.

---

### Post by cthk26 on 2008-03-02
OK, my install seems to be missing alsaconf (CLI)... I can run aconnectgui and the CLI versions of that but alsaconf is nowhere to be found.

Is it a bad install of ALSA, or has alsaconf been depreciated for something else in the latest version  perhaps?

---

### Post by Stochastic on 2008-03-02
you may want to try compiling ALSA from source (if that doesn't freak the noob in you out) to get an un-tweaked alsa setup that includes alsaconf (I don't think that's in the ubuntu version, but I'm no alsa guru).

---

### Post by cthk26 on 2008-03-04
I guess that's an option. Haven't compiled anything much in years but how hard can it be right? :lolflag:

---

