---
title: "[SOLVED] No sound for Newbie"
date: 2008-11-14
forum: Multimedia Software
---

### Post by Captonkirk on 2008-11-14
I recently installed ubuntu 8.10 and am new to linux. I'm not hearing any sound. I completed up to the step "Is my SoundCard supported?" at the following:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


Any help is appreciated. 



Here is part of the output for lspci -v | less:

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
        Subsystem: Dell Device 010e
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at c800 [size=256]
        I/O ports at cc40 [size=64]
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

02:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs Device 8022
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at dce0 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: EMU10K1_Audigy
        Kernel modules: snd-emu10k1

02:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
        Subsystem: Creative Labs Device 0020
        Flags: bus master, medium devsel, latency 64
        I/O ports at dcd8 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: Emu10k1_gameport
        Kernel modules: emu10k1-gp

---

### Post by Captonkirk on 2008-11-20
Using System > Preferences > Sound was able to configure sound card to play sound when pressing "Test" button or inserting audio CD into CD-ROM drive. But still no sound while online, either audio or video.

---

### Post by psyke83 on 2008-11-20
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Captonkirk on 2008-12-16
> **psyke83 said:**
> [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)


Used the tutorial at above thread to solve audio difficulties

---

