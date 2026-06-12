---
title: "Only one application can play sound at a time"
date: 2006-02-05
forum: Multimedia &amp; Video
---

### Post by mabster on 2006-02-05
Since I'm pretty new to Linux I'm not sure whether this is relating to my particular setup or something specific to Linux, thought I'd ask anyway ;) :

I've noticed that when one program is currently playing sound that another programs sound output will stop.  For example, while I've got XMMS playing my Gaim notification sounds won't play.  Sometimes XMMS will lose sound too and I have to switch tracks to get it to relinquish the sound device.  Is this normal?  Is there something I need to setup?  As far as I can tell, my sound should be setup properly.

My setup:
```
mabster@mab:~$ sudo lspci -s 0:1f.5 -vv
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 015f
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 17
        Region 0: I/O ports at b800 [size=256]
        Region 1: I/O ports at bc40 [size=64]
        Region 2: Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

mabster@mab:~$ sudo modprobe -l |grep ac97
/lib/modules/2.6.12-10-686-smp/kernel/sound/pci/ac97/snd-ak4531-codec.ko
/lib/modules/2.6.12-10-686-smp/kernel/sound/pci/ac97/snd-ac97-codec.ko
/lib/modules/2.6.12-10-686-smp/kernel/sound/oss/ac97_plugin_ad1980.ko
/lib/modules/2.6.12-10-686-smp/kernel/sound/oss/ac97.ko
/lib/modules/2.6.12-10-686-smp/kernel/sound/oss/ac97_codec.ko
mabster@mab:~$ sudo X -version

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux mab 2.6.12-10-686-smp #1 SMP Mon Jan 16 18:39:17 UTC 2006 i686
Build Date: 10 October 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-686-smp (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 SMP Mon Jan 16 18:39:17 UTC 2006 T
```

---

### Post by Adam83 on 2006-04-04
I am new to the Linux scene, but I thought I would add what I could.  I just tested and am able to to play sound in both Totem and Rhythmbox Musicplayer.  The sounds play concurrently and seem to be the same quality as if I were using the progams separately.  Which version of Ubuntu are you running?  Have you had any other problems with your sound?  Does sound play properly as long as it is only from one application at a time?  Under the "Multimedia Systems Selector", what sink and source do you have selected?
My source is OSS and sink is ESD.

---

