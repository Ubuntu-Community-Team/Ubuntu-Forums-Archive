---
title: "Audigy ZS pro MPU-401 MIDI input not working"
date: 2009-12-14
forum: Multimedia Software
---

### Post by Tricity on 2009-12-14
Can anybody help me with this:

Ubuntu Studio 9.10, quad-core Athlon system with 4GB, disabled on-board sound and installed an Audigy 2 ZS pro. My MIDI-USB devices (M-Audio) tended to cause kernel panics, so I tried to go through the game port of the Audigy with a MIDI-to-gameport cable. 

Sending MIDI _into_ the MPU-401 device (and out of the connector) works, but I cannot receive any MIDI commands _from_ an external device through the MPU-401 game port input. 

I observe the same effect with an old Fedora (5) and PlanetCCRMA, so I doubt that it is a driver issue.

Does anybody else have this problem? Could there be a special adapter cable needed? Or is it a persistent kernel driver problem in emu10k1_gp?

Any help appreciated!

---

### Post by Tricity on 2009-12-18
SOLVED!

The mpu-401 related file in the kernel sources needs to be patched. The file can be found for kernel 2.6.31-9-rt (that's ubuntu-studio 9.10) under .../sound/pci/emu10k1/emumpu401.c

At the end of this file, the UARTS get initialized in function snd_emu10k1_audigy_midi

Add this code:

        val = inl(emu->port + A_IOCFG);
        outl (val | A_IOCFG_GPOUT2, emu->port + A_IOCFG);
        udelay(10);
        outl (val, emu->port + A_IOCFG);

Compile the module (save your old snd-emu10k1.ko, just in case!), then replace it by the patched one.

---

