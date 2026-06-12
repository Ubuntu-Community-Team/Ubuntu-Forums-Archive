---
title: "Back with my sound problem"
date: 2008-09-02
forum: Multimedia Software
---

### Post by botokely on 2008-09-02
Again, here is my problem :

I've Xubuntu 8.04 installed on an Eee PC and I can't here any sound when or after xubuntu starts (if there is any sound cuz I've never heard anything :lolflag: ). I tried to access the sound settings but there is no button to turn the volume up and down. And it's amazing cuz I can play video and the sound works perfectly (and I can turn the volume up and down inside totem) :confused: .

I tried to follow the sound problem guide and here is what I've got:

botokely@trano:~$ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC662 Analog [ALC662 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
botokely@trano:~$ alsamixer

alsamixer: function snd_mixer_load failed: No such file or directory
botokely@trano:~$ amixer
amixer: Mixer default load error: No such file or directory
botokely@trano:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
botokely@trano:~$ lspci -vvx
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d9
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>
00: 86 80 90 25 06 00 90 20 04 00 00 06 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 d9 82
30: 00 00 00 00 e0 00 00 00 00 00 00 00 00 00 00 00

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d9
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at ec00 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
00: 86 80 92 25 07 00 90 00 04 00 00 03 00 00 80 00
10: 00 00 f0 f7 01 ec 00 00 08 00 00 d0 00 00 ec f7
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 d9 82
30: 00 00 00 00 d0 00 00 00 00 00 00 00 05 01 00 00

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d9
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Region 0: Memory at f7f80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>
00: 86 80 92 27 07 00 90 00 04 00 80 03 00 00 80 00
10: 00 00 f8 f7 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 d9 82
30: 00 00 00 00 d0 00 00 00 00 00 00 00 00 00 00 00

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82a1
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at f7eb8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
00: 86 80 68 26 06 00 10 00 04 00 03 04 04 00 00 00
10: 04 80 eb f7 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 a1 82
30: 00 00 00 00 50 00 00 00 00 00 00 00 05 01 00 00

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>
00: 86 80 60 26 04 05 10 00 04 00 04 06 04 00 81 00
10: 00 00 00 00 00 00 00 00 00 04 04 00 f0 00 00 20
20: f0 ff 00 00 f1 ff 01 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 05 01 06 00

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04) (prog-if 00 [Normal decode])
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fbf00000-fbffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>
00: 86 80 62 26 06 05 10 00 04 00 04 06 04 00 81 00
10: 00 00 00 00 00 00 00 00 00 03 03 00 f0 00 00 20
20: f0 fb f0 fb f1 ff 01 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 0b 02 06 00

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04) (prog-if 00 [Normal decode])
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
	Memory behind bridge: f8000000-fbefffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>
00: 86 80 64 26 06 05 10 00 04 00 04 06 04 00 81 00
10: 00 00 00 00 00 00 00 00 00 01 02 00 f0 00 00 20
20: 00 f8 e0 fb 01 f0 f1 f6 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 0a 03 06 00

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 4: I/O ports at e400 [size=32]
00: 86 80 58 26 05 00 80 02 04 00 03 0c 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 e4 00 00 00 00 00 00 00 00 00 00 43 10 d8 82
30: 00 00 00 00 00 00 00 00 00 00 00 00 03 01 00 00

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 20
	Region 4: I/O ports at e480 [size=32]
00: 86 80 59 26 05 00 80 02 04 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 81 e4 00 00 00 00 00 00 00 00 00 00 43 10 d8 82
30: 00 00 00 00 00 00 00 00 00 00 00 00 07 02 00 00

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at e800 [size=32]
00: 86 80 5a 26 05 00 80 02 04 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 e8 00 00 00 00 00 00 00 00 00 00 43 10 d8 82
30: 00 00 00 00 00 00 00 00 00 00 00 00 0a 03 00 00

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin D routed to IRQ 16
	Region 4: I/O ports at e880 [size=32]
00: 86 80 5b 26 05 00 80 02 04 00 03 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 81 e8 00 00 00 00 00 00 00 00 00 00 43 10 d8 82
30: 00 00 00 00 00 00 00 00 00 00 00 00 05 04 00 00

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at f7eb7c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
00: 86 80 5c 26 06 00 90 02 04 20 03 0c 00 00 00 00
10: 00 7c eb f7 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 d8 82
30: 00 00 00 00 50 00 00 00 00 00 00 00 03 01 00 00

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: <access denied>
00: 86 80 48 24 04 01 10 00 d4 01 04 06 00 00 01 00
10: 00 00 00 00 00 00 00 00 00 05 05 20 f0 00 80 22
20: f0 ff 00 00 f1 ff 01 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 50 00 00 00 00 00 00 00 ff 00 06 00

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
00: 86 80 41 26 07 00 00 02 04 00 01 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 d8 82
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04) (prog-if 80 [Master])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin B routed to IRQ 20
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
00: 86 80 53 26 05 00 b0 02 04 80 01 01 00 00 00 00
10: 01 00 00 00 01 00 00 00 01 00 00 00 01 00 00 00
20: a1 ff 00 00 00 00 00 00 00 00 00 00 43 10 d8 82
30: 00 00 00 00 70 00 00 00 00 00 00 00 00 02 00 00

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 0
	Region 4: I/O ports at 0400 [size=32]
00: 86 80 6a 26 01 00 80 02 04 00 05 0c 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 04 00 00 00 00 00 00 00 00 00 00 43 10 d8 82
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 02 00 00

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Unknown device 1a3b:1026
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
00: 8c 16 1c 00 07 00 10 00 01 00 00 02 04 00 00 00
10: 04 00 ef fb 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 01 50 00 00 3b 1a 26 10
30: 00 00 00 00 40 00 00 00 00 00 00 00 0a 01 00 00

03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8233
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 16 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at fbfa0000 [disabled] [size=128K]
	Capabilities: <access denied>
00: 69 19 48 20 06 00 10 00 a0 00 00 02 04 00 00 00
10: 04 00 fc fb 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 33 82
30: 00 00 fa fb 40 00 00 00 00 00 00 00 0b 01 00 00

botokely@trano:~$ 


Any help will be useful :-D

---

### Post by xeth_delta on 2008-09-02
Check if the sound card driver modules are loaded. To do that, open a terminal:
```
lsmod | grep snd
```

---

### Post by botokely on 2008-09-03
> **xeth_delta said:**
> Check if the sound card driver modules are loaded. To do that, open a terminal:
```
lsmod | grep snd
```

botokely@trano:~$ lsmod | grep snd

snd_hda_intel         344728  0 

snd_pcm_oss            42144  0 

snd_mixer_oss          17920  1 snd_pcm_oss

snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss

snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

snd_hwdep              10500  1 snd_hda_intel

snd_seq_dummy           4868  0 

snd_seq_oss            35584  0 

snd_seq_midi            9376  0 

snd_rawmidi            25760  1 snd_seq_midi

snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi

snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              24836  2 snd_pcm,snd_seq

snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

snd                    56996  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore               8800  1 snd

botokely@trano:~$

---

### Post by botokely on 2008-09-05
No suggestion anymore?

---

### Post by Crafty Kisses on 2008-09-05
Post this: ```
lspci -v
```

---

### Post by xeth_delta on 2008-09-05
> **botokely said:**
> botokely@trano:~$ lsmod | grep snd

snd_hda_intel         344728  0 

snd_pcm_oss            42144  0 

snd_mixer_oss          17920  1 snd_pcm_oss

snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss

snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

snd_hwdep              10500  1 snd_hda_intel

snd_seq_dummy           4868  0 

snd_seq_oss            35584  0 

snd_seq_midi            9376  0 

snd_rawmidi            25760  1 snd_seq_midi

snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi

snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              24836  2 snd_pcm,snd_seq

snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

snd                    56996  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore               8800  1 snd

botokely@trano:~$

Sorry for the delay, I have not been feeling very well.

The modules seem to be properly loaded and from your firsst post, I can see you do have the sound system from an intel chipset.

From your first post I can see it uses an ALC662 codec.
Let me check on the alsa documentation about the codec.

---

### Post by Yellow Pasque on 2008-09-05
Unless Xubuntu adds system sounds to Xfce, there are probably no sounds playing.
> [http://forum.xfce.org/index.php?topic=3032.0](http://forum.xfce.org/index.php?topic=3032.0)

---

### Post by xeth_delta on 2008-09-06
> **Temüjin said:**
> Unless Xubuntu adds system sounds to Xfce, there are probably no sounds playing.

That is true, please make sure it is in fact not working, before trying anyhting else.

Have you tried different sounds and unmuting from alsamixer?

If that fails try one of the following:
1.
```
sudo dpkg-reconfigure alsa-driver
```
reboot.

2.
Backup the config file
```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base-bk
```
edit the config file
```
sudo gedit /etc/modprobe.d/alsa-base
```
Add at the end of the file:
```
options snd-hda-intel model=model_type
```
Where you will replace model with one of the following:
```

          3stack-dig    3-stack (2-channel) with SPDIF
          3stack-6ch     3-stack (6-channel)
          3stack-6ch-dig 3-stack (6-channel) with SPDIF
          6stack-dig     6-stack with SPDIF
          lenovo-101e    Lenovo laptop
          eeepc-p701    ASUS Eeepc P701
          eeepc-ep20    ASUS Eeepc EP20
          auto          auto-config reading BIOS (default)

```
Start with auto, it will look like:
```
options snd-hda-intel model=auto
```
Restart the alsa service
```
sudo /etc/init.d/alsa-utils restart
```
or reboot.
If that does not work, try another model, and so on.
Let us know the results.

---

### Post by botokely on 2008-09-08
> **Codename said:**
> Post this: ```
lspci -v
```


Here is the results:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d9
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec00 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d9
	Flags: bus master, fast devsel, latency 0
	Memory at f7f80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82a1
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f7eb8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fbf00000-fbffffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
	Memory behind bridge: f8000000-fbefffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e400 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at e480 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f7eb7c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04) (prog-if 80 [Master])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: medium devsel
	I/O ports at 0400 [size=32]

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Unknown device 1a3b:1026
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8233
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at fbfa0000 [disabled] [size=128K]
	Capabilities: <access denied>


Thanks for any advice.

---

### Post by botokely on 2008-09-08
> **xeth_delta said:**
> That is true, please make sure it is in fact not working, before trying anyhting else.

Have you tried different sounds and unmuting from alsamixer?

If that fails try one of the following:
1.
```
sudo dpkg-reconfigure alsa-driver
```
reboot.

2.
Backup the config file
```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base-bk
```
edit the config file
```
sudo gedit /etc/modprobe.d/alsa-base
```
Add at the end of the file:
```
options snd-hda-intel model=model_type
```
Where you will replace model with one of the following:
```

          3stack-dig    3-stack (2-channel) with SPDIF
          3stack-6ch     3-stack (6-channel)
          3stack-6ch-dig 3-stack (6-channel) with SPDIF
          6stack-dig     6-stack with SPDIF
          lenovo-101e    Lenovo laptop
          eeepc-p701    ASUS Eeepc P701
          eeepc-ep20    ASUS Eeepc EP20
          auto          auto-config reading BIOS (default)

```
Start with auto, it will look like:
```
options snd-hda-intel model=auto
```
Restart the alsa service
```
sudo /etc/init.d/alsa-utils restart
```
or reboot.
If that does not work, try another model, and so on.
Let us know the results.

Thanks but before trying these commands I want to be sure of one thing : 
If normally there's no sound with Xfce so Xubuntu works as expected (but not as I've expected :))?!?
And cuz I've the sounds working properly when playing video (I can control the sound inside totem) I think (but I'm not sure) there's no problem at all.
BUT inside Xfce settings there is an item to control the sounds but there is no way to do this cuz there is no button to slide or something like this. So that's why I thought that something didn't match or didn't work :(
SO have I a sound problem or not :lolflag: ???

Sorry if I'm not very explicit with my bad english. I'm from a french speaking country.

And thanks a lot for being patient to answer me.

---

### Post by xeth_delta on 2008-09-08
> **botokely said:**
> Thanks but before trying these commands I want to be sure of one thing : 
If normally there's no sound with Xfce so Xubuntu works as expected (but not as I've expected :))?!?
And cuz I've the sounds working properly when playing video (I can control the sound inside totem) I think (but I'm not sure) there's no problem at all.
BUT inside Xfce settings there is an item to control the sounds but there is no way to do this cuz there is no button to slide or something like this. So that's why I thought that something didn't match or didn't work :(
SO have I a sound problem or not :lolflag: ???

Sorry if I'm not very explicit with my bad english. I'm from a french speaking country.

And thanks a lot for being patient to answer me.

Well, if you do have sound from music, I guess the drivers are not the problem at all. It seems to simply have something to do with the XFCE settings.

I am not a XFCE user, so I am not sure what that would be. What exactly are you trying to do? Sorry if you mentioned that before, I did not catch it.

---

