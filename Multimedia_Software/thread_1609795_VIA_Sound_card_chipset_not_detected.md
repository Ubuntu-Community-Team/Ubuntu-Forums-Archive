---
title: "VIA Sound card chipset not detected"
date: 2010-10-30
forum: Multimedia Software
---

### Post by Questor_ix on 2010-10-30
I got a new audio card today and Ubuntu 10.04 is not detecting it:

$ sudo lspci -v
05:06.0 Multimedia audio controller: VIA Technologies Inc. Device 0724 (rev 01)
        Subsystem: VIA Technologies Inc. Device 2403
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at a000 [size=32]
        I/O ports at a400 [size=128]
        Capabilities: [80] Power Management version 1

$ aplay -l
**** List of PLAYBACK Hardware Devices ****

I have looked at the sound card and it sports a VIA VT1723 chip. 

How can I get this working in Ubuntu?

---

### Post by Questor_ix on 2010-10-31
I upgraded Ubuntu to 10.10 in a vain hope that would help, but the situation is unchanged.

---

### Post by Yellow Pasque on 2010-10-31
You can try the alsaupgrade script: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
You'll need to use the -s option to get the latest snapshot so it will build on maverick. What kind of card is it?

---

