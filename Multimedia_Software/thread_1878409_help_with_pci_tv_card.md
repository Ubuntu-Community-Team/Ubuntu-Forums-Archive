---
title: "help with pci tv card"
date: 2011-11-09
forum: Multimedia Software
---

### Post by Anduan on 2011-11-09
Hello friends,
I have a problem with the pci card Medion PHILIPS Creatix CTX917 Analoge. I have no signal. I have tried a lot of things with tv time. mythtv, tv_me, but nothing at all.
I have ubuntu 11.04. I am bright new with linux and I am a little bit confused. 
  I will show you some details that could may help :

[PHP]kallia@kallia-desktop:~$ lspci -vv -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. PT880 Ultra/PT894 Host Bridge [1106:0308]
    Subsystem: ASRock Incorporation Device [1849:0308]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 8, Cache Line Size: 32 bytes
    Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-via

00:00.1 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:1308]
    Subsystem: ASRock Incorporation Device [1849:1308]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes

00:00.2 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:2308]
    Subsystem: ASRock Incorporation Device [1849:2308]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes

00:00.3 Host bridge [0600]: VIA Technologies, Inc. PT890 Host Bridge [1106:3208]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0

00:00.4 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:4308]
    Subsystem: ASRock Incorporation Device [1849:4308]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes

00:00.5 PIC [0800]: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller [1106:5308] (prog-if 20 [IO(X)-APIC])
    Subsystem: ASRock Incorporation Device [1849:5308]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes

00:00.7 Host bridge [0600]: VIA Technologies, Inc. PT894 Host Bridge [1106:7308]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes

00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198] (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-fe9fffff
    Prefetchable memory behind bridge: d0000000-dfffffff
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

00:02.0 PCI bridge [0604]: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller [1106:a208] (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 80000000-803fffff
    Prefetchable memory behind bridge: fdf00000-fdffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VT8237/8251 Serial ATA Controller [1106:5372] (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASRock Incorporation Device [1849:5372]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin B routed to IRQ 21
    Region 0: I/O ports at cc00 [size=8]
    Region 1: I/O ports at c880 [size=4]
    Region 2: I/O ports at c800 [size=8]
    Region 3: I/O ports at c480 [size=4]
    Region 4: I/O ports at c400 [size=16]
    Region 5: I/O ports at c000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sata_via
    Kernel modules: sata_via

00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 07) (prog-if 8a [Master SecP PriP])
    Subsystem: ASRock Incorporation K7VT2/K7VT6 motherboard [1849:0571]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
    Region 4: I/O ports at fc00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_via
    Kernel modules: pata_via

00:10.0 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0) (prog-if 00 [UHCI])
    Subsystem: ASRock Incorporation K7VT6 [1849:3038]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 20
    Region 4: I/O ports at b480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.1 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0) (prog-if 00 [UHCI])
    Subsystem: ASRock Incorporation K7VT6 [1849:3038]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 22
    Region 4: I/O ports at b800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.2 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0) (prog-if 00 [UHCI])
    Subsystem: ASRock Incorporation K7VT6 [1849:3038]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin C routed to IRQ 21
    Region 4: I/O ports at b880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.3 USB controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev b0) (prog-if 00 [UHCI])
    Subsystem: ASRock Incorporation K7VT6 [1849:3038]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin D routed to IRQ 23
    Region 4: I/O ports at bc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:10.4 USB controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 90) (prog-if 20 [EHCI])
    Subsystem: ASRock Incorporation K7VT6 motherboard [1849:3104]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin C routed to IRQ 21
    Region 0: Memory at fe8ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237S PCI to ISA Bridge [1106:3372]
    Subsystem: ASRock Incorporation Device [1849:3372]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Capabilities: <access denied>
    Kernel modules: i2c-viapro

00:11.7 Host bridge [0600]: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller [1106:287e]
    Subsystem: VIA Technologies, Inc. Device [1106:337e]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Capabilities: <access denied>

00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
    Subsystem: ASRock Incorporation K7VT6 motherboard [1849:3065]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (750ns min, 2000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 23
    Region 0: I/O ports at b000 [size=256]
    Region 1: Memory at fe8ff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: via-rhine
    Kernel modules: via-rhine

00:13.0 Host bridge [0600]: VIA Technologies, Inc. VT8237A Host Bridge [1106:337b]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>

00:13.1 PCI bridge [0604]: VIA Technologies, Inc. VT8237A PCI to PCI Bridge [1106:337a] (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fea00000-feafffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 SE] [1002:5964] (rev 01) (prog-if 00 [VGA controller])
    Subsystem: PC Partner Limited Device [174b:7c26]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
    Region 1: I/O ports at d000 [size=256]
    Region 2: Memory at fe9e0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at fe9c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon, radeonfb

01:00.1 Display controller [0380]: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) [1002:5d44] (rev 01)
    Subsystem: PC Partner Limited Device [174b:7c27]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 64 bytes
    Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

03:04.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 46) (prog-if 10 [OHCI])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
    Region 1: I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

03:05.0 Multimedia controller [0480]: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder [1131:7134] (rev 01)
    Subsystem: Creatix Polymedia GmbH Medion 7134 [16be:0003]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (21000ns min, 8000ns max)
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at feaff400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

03:06.0 Modem [0703]: PCTel Inc HSP56 MicroModem [134d:2189] (rev 04) (prog-if 00 [Generic])
    Subsystem: PCTel Inc Device [134d:1002]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping+ SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (250ns min, 15500ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at e800 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: serial

80:01.0 Audio device [0403]: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller [1106:3288] (rev 10)
    Subsystem: ASRock Incorporation Device [1849:0662]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 65
    Region 0: Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
[/PHP]
[PHP]kallia@kallia-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
usblp                  17827  0 
rt2870sta             410104  0 
snd_hda_codec_realtek   255882  1 
arc4                   12473  2 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
tda1004x               22897  0 
saa7134_alsa           18130  1 
snd_hwdep              13274  1 snd_hda_codec
tuner_simple           18134  1 
tuner_types            18907  1 tuner_simple
ir_lirc_codec          12770  0 
snd_pcm                80042  3 snd_hda_intel,snd_hda_codec,saa7134_alsa
lirc_dev               18720  1 ir_lirc_codec
tuner                  26802  1 
snd_seq_midi           13132  0 
ir_sony_decoder        12493  0 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
snd_rawmidi            25269  1 snd_seq_midi
ir_jvc_decoder         12490  0 
saa7134               149236  1 saa7134_alsa
rt2x00usb              19693  1 rt2800usb
snd_seq_midi_event     14475  1 snd_seq_midi
ir_rc6_decoder         12490  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
rc_core                25760  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,saa7134,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
v4l2_common            16757  2 tuner,saa7134
videodev               75143  3 tuner,saa7134,v4l2_common
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
snd                    55295  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,saa7134_alsa,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
soundcore              12600  1 snd
radeon                900524  3 
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
lp                     13349  0 
ttm                    65184  1 radeon
drm_kms_helper         40971  1 radeon
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
drm                   184164  5 radeon,ttm,drm_kms_helper
usbhid                 41704  0 
videobuf_dma_sg        18747  2 saa7134_alsa,saa7134
videobuf_core          25193  2 saa7134,videobuf_dma_sg
tveeprom               17009  1 saa7134
cfg80211              156212  2 rt2x00lib,mac80211
ppdev                  12849  0 
psmouse                73312  0 
parport_pc             32111  1 
serio_raw              12990  0 
parport                36746  3 lp,ppdev,parport_pc
i2c_viapro             12969  0 
i2c_algo_bit           13184  1 radeon
hid                    77084  1 usbhid
shpchp                 32345  0 
firewire_ohci          31504  0 
floppy                 60032  0 
sata_via               13464  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_via               13368  2 
via_rhine              27131  0 
[/PHP][PHP][ 5333.271470] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271491] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271514] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271533] hda-intel: spurious response 0x4011:0x0, last cmd=0x23903e
[ 5333.271553] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271574] hda-intel: spurious response 0x50:0x0, last cmd=0x23903e
[ 5333.271595] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271616] hda-intel: spurious response 0x4011:0x0, last cmd=0x23903e
[ 5333.271637] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271657] hda-intel: spurious response 0x4011:0x0, last cmd=0x23903e
[ 5333.271678] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271699] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271720] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271740] hda-intel: spurious response 0x4013:0x0, last cmd=0x23903e
[ 5333.271762] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271782] hda-intel: spurious response 0x4013:0x0, last cmd=0x23903e
[ 5333.271803] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271824] hda-intel: spurious response 0x50:0x0, last cmd=0x23903e
[ 5333.271844] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271867] hda-intel: spurious response 0x4013:0x0, last cmd=0x23903e
[ 5333.271887] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271907] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271927] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271948] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271969] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.271990] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272025] hda-intel: spurious response 0x4011:0x0, last cmd=0x23903e
[ 5333.272038] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272059] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272081] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272101] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272122] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272142] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272163] hda-intel: spurious response 0x80:0x0, last cmd=0x23903e
[ 5333.272184] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272204] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272226] hda-intel: spurious response 0x4015:0x0, last cmd=0x23903e
[ 5333.272248] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272267] hda-intel: spurious response 0x52:0x0, last cmd=0x23903e
[ 5333.272288] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272309] hda-intel: spurious response 0x4015:0x0, last cmd=0x23903e
[ 5333.272329] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272350] hda-intel: spurious response 0x54:0x0, last cmd=0x23903e
[ 5333.272371] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272392] hda-intel: spurious response 0x4015:0x0, last cmd=0x23903e
[ 5333.272413] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272434] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272454] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272475] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272496] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272517] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272538] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272558] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272579] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272602] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272621] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272642] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272662] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272684] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272704] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272725] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272746] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272766] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272787] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272808] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272829] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272850] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272870] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272891] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272912] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272933] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272953] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272976] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.272995] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273016] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273038] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273059] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273079] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273099] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273120] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273141] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273161] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273182] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273203] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273224] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273245] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273266] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273288] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273307] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273331] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273349] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273370] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273390] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273411] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273432] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273453] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273474] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273494] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273516] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273536] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273557] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273577] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273599] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273619] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273640] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273661] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273683] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273702] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273724] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273744] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273766] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273786] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273806] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273827] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273848] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273868] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273890] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273911] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273931] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273952] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273973] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.273994] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.274014] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.274035] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.274058] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 5333.274077] hda-intel: spurious response 0x0:0x0, last cmd=0x23903e
[ 8282.073145] hda-intel: spurious response 0x4011:0x0, last cmd=0x239037
[ 8282.073159] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073180] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073201] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073221] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073242] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073263] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073283] hda-intel: spurious response 0x80:0x0, last cmd=0x239037
[ 8282.073306] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073325] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073346] hda-intel: spurious response 0x4011:0x0, last cmd=0x239037
[ 8282.073367] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073387] hda-intel: spurious response 0x50:0x0, last cmd=0x239037
[ 8282.073409] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073429] hda-intel: spurious response 0x4011:0x0, last cmd=0x239037
[ 8282.073451] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073471] hda-intel: spurious response 0x50:0x0, last cmd=0x239037
[ 8282.073492] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073513] hda-intel: spurious response 0x4011:0x0, last cmd=0x239037
[ 8282.073533] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073555] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073575] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073595] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073616] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073637] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073660] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073680] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073699] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073720] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073741] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073762] hda-intel: spurious response 0x4011:0x0, last cmd=0x239037
[ 8282.073783] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073804] hda-intel: spurious response 0x50:0x0, last cmd=0x239037
[ 8282.073825] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073845] hda-intel: spurious response 0x4011:0x0, last cmd=0x239037
[ 8282.073865] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073890] hda-intel: spurious response 0x4011:0x0, last cmd=0x239037
[ 8282.073907] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073928] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073950] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.073970] hda-intel: spurious response 0x4013:0x0, last cmd=0x239037
[ 8282.073990] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074013] hda-intel: spurious response 0x4013:0x0, last cmd=0x239037
[ 8282.074032] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074053] hda-intel: spurious response 0x50:0x0, last cmd=0x239037
[ 8282.074074] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074095] hda-intel: spurious response 0x4013:0x0, last cmd=0x239037
[ 8282.074116] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074136] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074157] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074178] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074199] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074220] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074242] hda-intel: spurious response 0x4011:0x0, last cmd=0x239037
[ 8282.074262] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074282] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074304] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074323] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074344] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074365] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074388] hda-intel: spurious response 0x80:0x0, last cmd=0x239037
[ 8282.074407] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074427] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074449] hda-intel: spurious response 0x4015:0x0, last cmd=0x239037
[ 8282.074469] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074491] hda-intel: spurious response 0x52:0x0, last cmd=0x239037
[ 8282.074513] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074541] hda-intel: spurious response 0x4015:0x0, last cmd=0x239037
[ 8282.074564] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074579] hda-intel: spurious response 0x54:0x0, last cmd=0x239037
[ 8282.074595] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074617] hda-intel: spurious response 0x4015:0x0, last cmd=0x239037
[ 8282.074635] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074657] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074677] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074698] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074720] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074742] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074761] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074789] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074802] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074822] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074844] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074865] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074885] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074906] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074927] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074947] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074969] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.074988] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075010] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075031] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075056] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075072] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075092] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075116] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075134] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075155] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075176] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075196] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075217] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075238] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075259] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075280] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075302] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075324] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075342] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075363] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075384] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075405] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075426] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075446] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075469] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075488] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075509] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075530] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075550] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075571] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075592] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075613] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075634] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075657] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075675] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075696] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075718] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075738] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075759] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075779] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075800] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075822] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075844] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075863] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075884] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075905] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075927] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075946] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075971] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.075991] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076019] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076036] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076058] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076077] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076098] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076118] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076139] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076160] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076181] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076203] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076222] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076244] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076264] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076285] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076306] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076327] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076347] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076368] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076389] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076412] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076431] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076451] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076472] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076493] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076514] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076535] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076557] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076576] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076597] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076617] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076638] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076659] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076680] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076701] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076721] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076742] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076763] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076784] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076805] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076825] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076846] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076867] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076889] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076910] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.076932] hda-intel: spurious response 0x0:0x0, last cmd=0x239037
[ 8282.552282] hda-intel: spurious response 0x4011:0x0, last cmd=0x239033
[ 8282.552303] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552320] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552343] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552361] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552382] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552403] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552423] hda-intel: spurious response 0x80:0x0, last cmd=0x239033
[ 8282.552444] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552465] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552486] hda-intel: spurious response 0x4011:0x0, last cmd=0x239033
[ 8282.552508] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552577] hda-intel: spurious response 0x50:0x0, last cmd=0x239033
[ 8282.552580] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552582] hda-intel: spurious response 0x4011:0x0, last cmd=0x239033
[ 8282.552594] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552612] hda-intel: spurious response 0x50:0x0, last cmd=0x239033
[ 8282.552633] hda-intel: spurious response 0x0:0x0, last cmd=0x239033
[ 8282.552695] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552716] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552737] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552757] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552778] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552799] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552820] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552841] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552862] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552882] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552904] hda-intel: spurious response 0x4011:0x0, last cmd=0x239032
[ 8282.552924] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552947] hda-intel: spurious response 0x50:0x0, last cmd=0x239032
[ 8282.552966] hda-intel: spurious response 0x0:0x0, last cmd=0x239032
[ 8282.552987] hda-intel: spurious response 0x4011:0x0, last cmd=0x239032
[ 8282.553049] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553070] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553091] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553112] hda-intel: spurious response 0x4013:0x0, last cmd=0x239031
[ 8282.553132] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553153] hda-intel: spurious response 0x4013:0x0, last cmd=0x239031
[ 8282.553174] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553195] hda-intel: spurious response 0x50:0x0, last cmd=0x239031
[ 8282.553216] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553237] hda-intel: spurious response 0x4013:0x0, last cmd=0x239031
[ 8282.553257] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553278] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553299] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553322] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553341] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553362] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553383] hda-intel: spurious response 0x4011:0x0, last cmd=0x239031
[ 8282.553404] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553425] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553445] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553467] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553491] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553508] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553528] hda-intel: spurious response 0x80:0x0, last cmd=0x239031
[ 8282.553550] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553571] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553591] hda-intel: spurious response 0x4015:0x0, last cmd=0x239031
[ 8282.553612] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553636] hda-intel: spurious response 0x52:0x0, last cmd=0x239031
[ 8282.553653] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553677] hda-intel: spurious response 0x4015:0x0, last cmd=0x239031
[ 8282.553695] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553717] hda-intel: spurious response 0x54:0x0, last cmd=0x239031
[ 8282.553737] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553757] hda-intel: spurious response 0x4015:0x0, last cmd=0x239031
[ 8282.553778] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553800] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553820] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553841] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553862] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553882] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553903] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553925] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553945] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553966] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.553989] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554007] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554030] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554049] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554069] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554091] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554112] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554132] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554153] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554175] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554195] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554215] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554236] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554258] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554278] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554299] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554320] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554341] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554362] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554381] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554404] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554423] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554443] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554464] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554485] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554506] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554527] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554548] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554569] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554589] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554610] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554631] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554651] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554673] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554694] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554714] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554734] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554758] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554778] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554797] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554819] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554839] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554860] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554880] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554901] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554923] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554944] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554963] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.554984] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555006] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555026] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555046] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555068] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555088] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555110] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555132] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555151] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555171] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555193] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555213] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555234] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555259] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555276] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555296] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555317] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555338] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555359] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555380] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555400] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555421] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555441] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555462] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555485] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555504] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555524] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555546] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555567] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555587] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555619] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555629] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555660] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555670] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555691] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555719] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555733] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555755] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555774] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555796] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555816] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555838] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555860] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555881] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555900] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555920] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555941] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555962] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.555983] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556021] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556029] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556050] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556070] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556091] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556111] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556134] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556153] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556174] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556194] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556217] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556236] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556257] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556278] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556298] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8282.556319] hda-intel: spurious response 0x0:0x0, last cmd=0x239031
[ 8663.935264] show_signal_msg: 18 callbacks suppressed
[ 8663.935271] zapping[3927]: segfault at 7661024 ip 01a4fa41 sp bffd2238 error 6 in libc-2.13.so[193c000+15a000]
[ 8696.683517] zapping[3951]: segfault at 8331024 ip 04775a41 sp bfb773a8 error 6 in libc-2.13.so[4662000+15a000]
[ 8709.848293] zapping[3963]: segfault at 251c024 ip 0863ea41 sp bfbe9a28 error 6 in libc-2.13.so[852b000+15a000]
[ 8715.423656] zapping[3975]: segfault at 1440024 ip 06b85a41 sp bfa7b118 error 6 in libc-2.13.so[6a72000+15a000]
[ 8720.034526] zapping[3986]: segfault at 16f5024 ip 06430a41 sp bfe01888 error 6 in libc-2.13.so[631d000+15a000]
[/PHP]

Thanx in advance for any help

---

### Post by BicyclerBoy on 2011-11-10
Most analogue tuner drivers were broken with kernel changes to v4l v4l2 headers/modules.
These kernel changes have made their way back into 10.04 & possibly 10.04.

[http://www.kernellabs.com/blog/?p=1517](http://www.kernellabs.com/blog/?p=1517)
[http://linuxtv.org/wiki/index.php/News_Archive](http://linuxtv.org/wiki/index.php/News_Archive)

Your h/w would be supported by older version of Ubuntu.
Or it should be possible to build the old v4l modules..

look in the output of: 
dmesg

edit:
A quick search of LinuxTV etc shows **no** support for your card..

---

### Post by Anduan on 2011-11-10
Thanks a lot BicyclerBoy,

it sounds a little bad. 
The only question that I have is, why tv_time claims that every tv tuner with philips saa7134 chipset, works on ubuntu?


the command  dmesg | grep saa7134 gives this:

> kallia@kallia-desktop:~$ dmesg | grep saa7134
[   16.300333] saa7134 0000:03:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.300341] saa7134[0]: found at 0000:03:05.0, rev: 1, irq: 18, latency: 32, mmio: 0xfeaff400
[   16.300348] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,autodetected]
[   16.300360] saa7134[0]: board init: gpio is 0
[   16.480385] saa7134[0]: i2c eeprom 00: be 16 03 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   16.480397] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[   16.480407] saa7134[0]: i2c eeprom 20: 01 40 01 02 02 03 01 00 06 ff 00 1f 02 51 96 2b
[   16.480417] saa7134[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[   16.480427] saa7134[0]: i2c eeprom 40: ff 1d 00 c2 86 10 01 01 00 00 fd 79 44 9f c2 8f
[   16.480437] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff 06 06 0f 00 0f 00 0f 00 0f 00
[   16.480447] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.480456] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.480466] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.480476] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.480486] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.480496] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.480505] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.480515] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.480525] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.480534] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.504049] saa7134[0] Board has DVB-T
[   16.504054] saa7134[0] Tuner type is 63
[   16.540171] tuner 6-0061: chip found @ 0xc2 (saa7134[0])
[   16.672360] saa7134[0]: registered device video0 [v4l2]
[   16.672471] saa7134[0]: registered device vbi0
[   16.672602] saa7134[0]: registered device radio0
[   16.688953] saa7134 ALSA driver for DMA sound loaded
[   16.691498] saa7134[0]/alsa: saa7134[0] at 0xfeaff400 irq 18 registered as card -2
[   16.832162] DVB: registering new adapter (saa7134[0])


Could you suggest me some cheap tv tuners that are going to work with ubuntu 11.04?
I just want to watch analog TV and nothing else more.


thank you for your time.

---

### Post by BicyclerBoy on 2011-11-11
I couldn't find anything by searching for medion or "16be:0003".
But your dmesg output info looks promising..

Make sure you have the non-free firmware package installed.
Your card should have a firmware cold-start loading event from power-off reset cycle. Or a warm state event etc..

If the V4l changes have broken the analogue support, you could still try the dvb-t (digital terrestial OTA) input ?

I don't know what your card is/has but..
The analogue input could be used for analogue TV (this is switching off round the world) or composite/s-video input.

---

### Post by Anduan on 2011-11-13
ok but how can I check that non-free firmware package is installed? Sorry for this question but I am very new with ubuntu. And what is non-free firmware?

---

### Post by BicyclerBoy on 2011-11-14
Non-free firmware must be installed..

Run synaptic package manager
search for linux-non-free or firmware..
"linux-firmware"
"linux-firmware-nonfree"
Your device may use the "free" firmware..don't know.
My dvb-t nova-500-t seems to use "free"..

The non-free means not open source &/or not free to copy under GPL.
Does not necessary mean illegal or stolen.
Just not allowed to be in the std ubuntu GPL distro.

---

### Post by Anduan on 2011-11-14
I found and installed the firmware about television but I still have no signal. Here is a picture of what I have done.
[]("http://ubuntuforums.org/static.panoramio.com/photos/original/62154483.jpg")[http://static.panoramio.com/photos/original/62154483.jpg](http://static.panoramio.com/photos/original/62154483.jpg)[URL="http://ubuntuforums.org/static.panoramio.com/photos/original/62154483.jpg"]
[/URL]

---

### Post by Anduan on 2011-11-14
IT IS ALIIIIIIIIIIVEE yes I have picture finaly. :D  

But it is black and white and without sound ...:confused:

 You help me a lot BicyclerBoy thank you very much. Now I have to configure what to do,to have also sound and color

---

### Post by BicyclerBoy on 2011-11-14
If you get b&w & no audio with analogue TV then...
- likely have incorrect TV standard.

PAL <--> NTSC-M : no colour (wrong colour format & AM carrier offset)

PAL B <--> PAL K   ?  no audio due to audio FM sub-carrier offset (can be 4.5 -6 MHz)

Th audio problem could be solved by finding the audio input device in dmesg.

---

### Post by Anduan on 2011-11-14
the good news are that I found the color by changing form secam to pal, but the bad news are when I restart my computer all gone. Now I have no signal again.. I think that something wrong is going with my computer, as when I restart  it, the most of the times it does not recognize my audio card.  And I make a lot of restarts to recognize it.
The same happens  also with the TV tuner some times it does not recognize it and TVtime does not give me the option to search for channels.

---

### Post by BicyclerBoy on 2011-11-14
Secam was only used in France & Russia (& may be some poor ex French administrated African countries)

Could be problem with sequence on startup..

Try
sudo modprobe saa7134

Then look at dmesg to see if the card detection/firmware/registering worked..

(use your previous dmesg or a working reboot as "good")

---

### Post by Anduan on 2011-11-14
After a lot of restarts ubuntu mange to recognize audio card and tv tuner, so I have picture again. 
And also after a lot of search I mange to have audio using the command for the terminal : "pactl load-module module-loopback" that worked for me from the forum [https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770](https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770). Also I changed the audio standard to PAL-BG from the channel manager 

finaly the tv tuner worked ! ! Thank you BicyclerBoy for your help

---

### Post by Anduan on 2011-11-15
at the times that tvtime does not respond, I try sudo modprobe saa7134 and then I look at the dmesg and it seems that tvtuner does not recognized. So I keep doing a lot of reboots until the time that is being recognized. I do not know how to do it manually. And also the same thing happens with the on board sound card the most of the time does not being recognized after a reboot.

---

### Post by Anduan on 2011-11-17
well there are three options with my problem. The time that ubuntu recognize the tv tuner the dmesg | grep saa7134 gives 

[PHP]allia@kallia-desktop:~$ dmesg | grep saa7134
[   16.279731] saa7134 0000:03:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.279738] saa7134[0]: found at 0000:03:04.0, rev: 1, irq: 17, latency: 32, mmio: 0xfeaffc00
[   16.279745] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,autodetected]
[   16.279759] saa7134[0]: board init: gpio is 0
[   16.436035] saa7134[0]: i2c eeprom 00: a2 14 00 00 04 20 10 00 43 40 a8 14 00 82 b2 92
[   16.436046] saa7134[0]: i2c eeprom 10: 00 80 82 00 30 00 b8 00 00 40 32 50 00 14 00 50
[   16.436061] saa7134[0]: i2c eeprom 20: 00 00 01 02 02 03 00 00 02 8d 00 00 00 50 92 00
[   16.436074] saa7134[0]: i2c eeprom 30: a0 10 00 17 00 82 80 1e 42 50 00 11 00 83 b2 00
[   16.436088] saa7134[0]: i2c eeprom 40: 9c 00 00 40 00 10 00 01 00 00 f8 39 40 94 80 05
[   16.436102] saa7134[0]: i2c eeprom 50: 04 d5 b8 15 01 d4 00 04 01 00 0c 00 0f 00 0b 00
[   16.436116] saa7134[0]: i2c eeprom 60: e8 58 5b 89 fa 00 01 50 22 81 e2 02 00 d4 b8 15
[   16.436129] saa7134[0]: i2c eeprom 70: 01 77 f0 97 bd 9f fe 5b 02 89 fb 00 01 50 22 81
[   16.436143] saa7134[0]: i2c eeprom 80: fa 01 00 d4 bc 14 04 d4 b8 15 01 83 fa ff fe 58
[   16.436157] saa7134[0]: i2c eeprom 90: 5a 8d e2 00 00 51 a2 d4 b8 15 01 83 fa ff ef 58
[   16.436171] saa7134[0]: i2c eeprom a0: 5a 8d e2 00 00 50 b1 d4 b8 14 04 77 f0 c3 1f d4
[   16.436185] saa7134[0]: i2c eeprom b0: b8 15 02 83 fa c7 ff 96 bc 9b 7a 52 40 d4 b8 14
[   16.436198] saa7134[0]: i2c eeprom c0: 04 77 f0 c3 1f d4 b8 15 02 51 90 d4 b8 15 01 83
[   16.436212] saa7134[0]: i2c eeprom d0: fa ff ef 58 5a 8d e2 00 00 50 b1 d4 b8 14 04 77
[   16.436226] saa7134[0]: i2c eeprom e0: f0 c3 1f d4 b8 15 04 83 fa c7 ff 96 bc 9b 7a 50
[   16.436240] saa7134[0]: i2c eeprom f0: a0 d4 b8 14 04 77 f0 c3 1f d4 b8 15 04 83 fa f8
[   16.452056] saa7134[0] Cant determine tuner type 5b52 from EEPROM
[   16.452063] saa7134[0] Tuner type is 63
[   16.559719] tuner 1-0043: chip found @ 0x86 (saa7134[0])
[   16.612094] tuner 1-0061: chip found @ 0xc2 (saa7134[0])
[   16.736395] saa7134[0]: registered device video0 [v4l2]
[   16.736541] saa7134[0]: registered device vbi0
[   16.736666] saa7134[0]: registered device radio0
[   16.777058] saa7134 ALSA driver for DMA sound loaded
[   16.777099] saa7134[0]/alsa: saa7134[0] at 0xfeaffc00 irq 17 registered as card -2
[   16.972044] DVB: registering new adapter (saa7134[0])
kallia@kallia-desktop:~$ [/PHP]

when ubuntu does not recognize the tv card the dmesg | grep saa7134 gives

[PHP]kallia@kallia-desktop:~$ dmesg | grep saa7134
[   16.318855] saa7134 0000:03:04.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.318862] saa7134[0]: found at 0000:03:04.0, rev: 1, irq: 17, latency: 32, mmio: 0xfeaffc00
[   16.318870] saa7134[0]: subsystem: 108c:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   16.318889] saa7134[0]: board init: gpio is 0
[   16.491435] saa7134[0]: i2c eeprom 00: a2 14 00 00 04 20 10 00 43 40 a8 14 00 82 b2 92
[   16.491446] saa7134[0]: i2c eeprom 10: 00 80 82 00 30 00 b8 00 00 40 32 50 00 14 00 50
[   16.491456] saa7134[0]: i2c eeprom 20: 00 00 01 02 02 03 00 00 02 8d 00 00 00 50 92 00
[   16.491466] saa7134[0]: i2c eeprom 30: a0 10 00 17 00 82 80 1e 42 50 00 11 00 83 b2 00
[   16.491476] saa7134[0]: i2c eeprom 40: 9c 00 00 40 00 10 00 01 00 00 f8 39 40 94 80 05
[   16.491486] saa7134[0]: i2c eeprom 50: 04 d5 b8 15 01 d4 00 04 01 00 0c 00 0f 00 0b 00
[   16.491496] saa7134[0]: i2c eeprom 60: e8 58 5b 89 fa 00 01 50 22 81 e2 02 00 d4 b8 15
[   16.491505] saa7134[0]: i2c eeprom 70: 01 77 f0 97 bd 9f fe 5b 02 89 fb 00 01 50 22 81
[   16.491515] saa7134[0]: i2c eeprom 80: fa 01 00 d4 bc 14 04 d4 b8 15 01 83 fa ff fe 58
[   16.491525] saa7134[0]: i2c eeprom 90: 5a 8d e2 00 00 51 a2 d4 b8 15 01 83 fa ff ef 58
[   16.491535] saa7134[0]: i2c eeprom a0: 5a 8d e2 00 00 50 b1 d4 b8 14 04 77 f0 c3 1f d4
[   16.491545] saa7134[0]: i2c eeprom b0: b8 15 02 83 fa c7 ff 96 bc 9b 7a 52 40 d4 b8 14
[   16.491555] saa7134[0]: i2c eeprom c0: 04 77 f0 c3 1f d4 b8 15 02 51 90 d4 b8 15 01 83
[   16.491565] saa7134[0]: i2c eeprom d0: fa ff ef 58 5a 8d e2 00 00 50 b1 d4 b8 14 04 77
[   16.491575] saa7134[0]: i2c eeprom e0: f0 c3 1f d4 b8 15 04 83 fa c7 ff 96 bc 9b 7a 50
[   16.491584] saa7134[0]: i2c eeprom f0: a0 d4 b8 14 04 77 f0 c3 1f d4 b8 15 04 83 fa f8
[   16.495970] saa7134[0]: registered device video0 [v4l2]
[   16.496305] saa7134[0]: registered device vbi0
[   16.516976] saa7134 ALSA driver for DMA sound loaded
[   16.517016] saa7134[0]/alsa: saa7134[0] at 0xfeaffc00 irq 17 registered as card -2
kallia@kallia-desktop:~$ 
[/PHP]

and when ubuntu recognize the tv tuner but the TVtime does not find channels the dmesg | grep saa7134 gives

[PHP]kallia@kallia-desktop:~$ dmesg | grep saa7134
[   15.775744] saa7134 0000:03:06.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.775752] saa7134[0]: found at 0000:03:06.0, rev: 1, irq: 19, latency: 32, mmio: 0xfeaffc00
[   15.775759] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,autodetected]
[   15.775776] saa7134[0]: board init: gpio is 0
[   15.932467] saa7134[0]: i2c eeprom 00: be 16 03 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   15.932479] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[   15.932489] saa7134[0]: i2c eeprom 20: 01 40 01 02 02 03 01 00 06 ff 00 1f 02 51 96 2b
[   15.932499] saa7134[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[   15.932509] saa7134[0]: i2c eeprom 40: ff 1d 00 c2 86 10 01 01 00 00 fd 79 44 9f c2 8f
[   15.932519] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff 06 06 0f 00 0f 00 0f 00 0f 00
[   15.932529] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.932539] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.932548] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.932558] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.932568] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.932578] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.932588] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.932598] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.932607] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.932617] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.957329] saa7134[0] Board has DVB-T
[   15.957333] saa7134[0] Tuner type is 63
[   15.992231] tuner 1-0061: chip found @ 0xc2 (saa7134[0])
[   16.069332] saa7134[0]: registered device video0 [v4l2]
[   16.069530] saa7134[0]: registered device vbi0
[   16.069669] saa7134[0]: registered device radio0
[   16.138680] saa7134 ALSA driver for DMA sound loaded
[   16.138724] saa7134[0]/alsa: saa7134[0] at 0xfeaffc00 irq 19 registered as card -2
[   16.212039] DVB: registering new adapter (saa7134[0])
kallia@kallia-desktop:~$ 
[/PHP]

In second option when the tv tuner is recognized as unknown/generic  from ubuntu I tried to uninstall the tv tuner from kernel with the commands

 "rmmod saa7134" but I take the message "ERROR: Module saa7134 is in use by saa7134_alsa"

and with "modprobe -r saa7134" I take the message
"FATAL: Module saa7134 is in use."

so I can not uninstal the tvcard and install from the beginning with the correct card number ant tuner number. 

please help ubuntu musters, i need your help

---

### Post by BicyclerBoy on 2011-11-19
When the tuner card does not work..the dmesg shows the PCI card is incorrectly identified..it has the wrong PCI ID..

There is no way to fix/recover if the kernel can not correctly report the the hardware.

I would get rid of the VIA chipset mobo..
May be there is some kernel/grub cmd option to work-around h/w reporting problems on your chipset ??
If not then this h/w is a lost cause..

---

### Post by Anduan on 2011-11-19
after all I found this magic command "echo saa7134 card=12 | sudo tee -a /etc/modules" from the thread [http://askubuntu.com/questions/19849/how-do-you-setup-the-driver-for-a-philips-based-tv-capture-card]("http://askubuntu.com/questions/19849/how-do-you-setup-the-driver-for-a-philips-based-tv-capture-card") 
That worked for me, as I know the right number of my card. And it works every time when I boot. 

About the sound I use the command "sudo alsa force-reload" for the times that I boot and I have no sound. 

And to link the audio input of the tv card with the audio output of the sound card I use the command "pactl load-module module-loopback"  

And thats all folks ! ! !

Of course all these are not user friendly, but as I can understand this is the philosophy of linux. I express this comment as I am bright new with ubuntu, and I have a lot of  ? ? ? ?  I wish in the future Linux could be more friendly as it is a very powerful O.S.

---

