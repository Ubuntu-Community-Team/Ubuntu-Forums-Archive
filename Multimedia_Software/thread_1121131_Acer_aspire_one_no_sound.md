---
title: "Acer aspire one no sound"
date: 2009-04-09
forum: Multimedia Software
---

### Post by hutchic on 2009-04-09
Ubuntu 8.10

Linux 2.6.27-11-generic

Acer aspire one D150

Asla version 1.0.19

asla-info.sh script output can be located here 
[http://www.alsa-project.org/db/?f=2fa5e35e7df9e526c57f40d4cffa449869f68a2d](http://www.alsa-project.org/db/?f=2fa5e35e7df9e526c57f40d4cffa449869f68a2d)

Some more information that may be of use.  I'm pretty sure the asla-info script is very thorough.  If nobody here has any advice I'll likely make a post on the asla bug board.

colin@colin-laptop:~$ aplay -l 
**** List of PLAYBACK Hardware Devices **** 
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 


colin@colin-laptop:~$ lspci -vv | less 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
        Subsystem: Acer Incorporated [ALI] Device 019c 
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0 
        Interrupt: pin A routed to IRQ 16 
        Region 0: Memory at 56340000 (64-bit, non-prefetchable) [size=16K] 
        Capabilities: <access denied> 
        Kernel driver in use: HDA Intel 
        Kernel modules: snd-hda-intel 


colin@colin-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec 
Codec: Realtek ALC272 

colin@colin-laptop:~$ uname -a 
Linux colin-laptop 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux 

colin@colin-laptop:~$ dmesg | grep 00:1b.0 
[    0.888558] PCI: 0000:00:1b.0 reg 10 64bit mmio: [56340000, 56343fff] 
[    0.888558] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold 
[    0.888558] pci 0000:00:1b.0: PME# disabled 
[   20.083109] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   20.083161] HDA Intel 0000:00:1b.0: setting latency timer to 64

---

### Post by hutchic on 2009-04-14
Installed the Ubuntu Netbook remix and sound works in it.

---

### Post by spsmiler on 2009-09-22
[SIZE=3]I use UNR and although I hear sounds when logging in the machine falls silent once I've logged in.

Anyone have any *simple* (please) ideas on how I get get the sound to work all the time??

TIA

Simon[/SIZE]  :confused:

---

