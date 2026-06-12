---
title: "ALSA - no soundcards loaded"
date: 2014-11-15
forum: Multimedia Software
---

### Post by rayalexie on 2014-11-15
Pretext: on this SAME SYSTEM, no more than three hours ago, sound through ALSA worked fine in Lubuntu 14.04 (lubuntu-desktop).  I wanted to switch to an even more minimal system: ubuntu minimal install, followed by xorg and openbox, and using startx after the tty1 login.  This issue only arose in THIS openbox-only environment (openbox-session).

Sound refuses to work in alsa.  Alsa refuses to identify or acknowledge my devices.  However, some config files do acknowledge my devices, and the sound modules are loaded.

I purged and re-installed alsa-base, alsa-utils, linux-sound-base.  No changes.

Additional info, which applies to both the old Lubuntu and current openbox-session setups: using the fglrx drivers from the Trusty repos.  

Guidance would be appreciated.

```

aplay: device_list:268: no soundcards found...

```
```

sudo lshw -C sound

  *-multimedia:0          
       description: Audio device
       product: Wrestler HDMI Audio
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1.1
       bus info: pci@0000:00:01.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:41 memory:feb44000-feb47fff
  *-multimedia:1
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:16 memory:feb40000-feb43fff


```
```

cat /proc/asound/cards

 0 [Generic        ]: HDA-Intel - HD-Audio Generic

                      HD-Audio Generic at 0xfeb44000 irq 41

 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfeb40000 irq 16


```
```

# a segment from lspci -vv
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7698
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 41
    Region 0: Memory at feb44000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    **Kernel driver in use: snd_hda_intel**

```
```

Linux MyPC 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


```
 
If this has something to do with a lockout due to me not specifically using a *buntu desktop, please let me know now so that I can abandon Ubuntu.

---

### Post by Rob Sayer on 2014-11-16
Haven't had much experience with this specifically but did you install gnome-alsamixer?

BTW fglrx is the proprietary video driver for AMD Radeon video cards and I don't think that'd have anything to do with your problem.

---

### Post by rayalexie on 2014-11-22
I appreciate your reply.  I want to shy away from gnome dependencies, so no; alsamixer suffices.  I only mentioned the graphics driver because, unless I'm mistaken, it does play some role in HDMI sound output.

---

### Post by Yellow Pasque on 2014-11-25
Maybe with a minimal/no-pulseaudio setup, you need to manually add your user to the "audio" permissions group?

---

