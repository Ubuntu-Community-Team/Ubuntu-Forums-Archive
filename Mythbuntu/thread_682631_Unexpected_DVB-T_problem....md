---
title: "Unexpected DVB-T problem..."
date: 2008-01-30
forum: Mythbuntu
---

### Post by Ubeast on 2008-01-30
Hi,

I'm having problems with a new built of Mythbuntu where I cannot get either of my two DVB-T cards to load.

Background:

The cards in question are:
DVICO Fusion DVB-T Plus
Avermedia AverTV DVB-T 771

As far as I know both of them use the same module under linux, and in the past both have identified themselves as DVICO cards (even the Avermedia).

I have been using these cards successfully for some time just using 'out of the box' driver support in the latest kernels - so my current problem has me 
scratching my head to say the least.

For info I run a combined backend/frontend.

Until yesterday I was running on a fully Ubuntu install, initially Fiesty, then Gutsy. The install was getting a little old and I wanted to try Mythbuntu, 
so I did a clean install of Mythbuntu 7.10 from the livecd. Everything went well and I had two functioning DVB cards, correctly configured in Mythtv-setup 
and working perfectly in the Frontend.

Unfortunately, I couldn't leave well enough alone and stipped the computer down for some annual component dusting. At this point my motherboard decided not 
to play anymore and promptly stopped recognising the CPU.

So today I found someone selling basically the exact same motherboard secondhand with a faster CPU so I quickly snapped it up and threw it all together 
tonight.

The only difference in hardware from my old system (which worked fine) is:

Motherboard changed from  DFI Lanparty UT SLI-DR to DFI Lanparty UT Ultra-D
The only difference between these two boards is the Ultra-D doesn't have Raid (so 4 less sata connectors) and doesn't support SLI (which I didn't use before 
anyway). I also changed the CPU from an AMD64 3200+ to AMD64 3800+.

In practice, the motherboard is identical and the cards all went back in the same slots I used to use them in before.

So long story short(er), when I performed a clean install on Mythbuntu 7.10 tonight, it appeared to all go well - until I tried to add the capture cards in 
mythtv-setup. They aren't there (unable to open card) as they normally would be at this point and there is nothing under /dev/dvb/. Damn.

For fault finding I took the Avermedia card out and left the Dvico in.

A check of lspci reveals the card is seen at least:

```
01:06.0 Non-VGA unclassified device: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: DViCO Corporation FusionHDTV DVB-T Plus
        Flags: medium devsel, IRQ 11
        Capabilities: <access denied>

01:06.2 Unclassified device [0080]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: DViCO Corporation Unknown device db11
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
```

dmesg | grep dvb reveals:

```
[   43.624321] cx2388x dvb driver version 0.0.6 loaded
[   43.624324] cx8802_register_driver() ->registering driver type=dvb access=shared
[   43.624330] cx88[0]/2: cx2388x based dvb card
[   44.161359] cx8802_dvb_probe dvb_register failed err = -1
```

dmesg | grep cx reveals:

```
[   43.276835] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[   43.276893] CORE cx88[0]: subsystem: 18ac:db11, board: DViCO FusionHDTV DVB-T Plus [card=21,autodetected]
[   43.503303] cx2388x v4l2 driver version 0.0.6 loaded
[   43.533377] cx88[0]/2: cx2388x 8802 Driver Manager
[   43.533592] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 20, latency: 32, mmio: 0x40000000
[   43.557446] cx8800: probe of 0000:01:06.0 failed with error -5
[   43.624321] cx2388x dvb driver version 0.0.6 loaded
[   43.624324] cx8802_register_driver() ->registering driver type=dvb access=shared
[   43.624327] CORE cx88[0]: subsystem: 18ac:db11, board: DViCO FusionHDTV DVB-T Plus [card=21]
[   43.624330] cx88[0]/2: cx2388x based dvb card
[   44.161357] cx88[0]: frontend initialization failed
[   44.161359] cx8802_dvb_probe dvb_register failed err = -1
[   44.161361] cx8802_register_driver() ->probe failed err = -1
```

When I peruse kern.log I find a few interesting lines but I'm not smart enough to make sense of all this (hence why I'm posting here). It's leading me to think it's an irq related problem or something along those lines. I've been through my bios looking for any obvious culprits, and I've tried to match the settings as close as I remember the other motherboard being (which is now dead so I can't check). In any case, usless stuff like FDD controller, Serial ports, IR etc are all disabled.

I'd really love some help here, I KNOW these cars work under current builds of Ubuntu, and in fact were working under Mythbuntu 7.10 only 24hrs ago.

Much obliged...

Jesse

---

### Post by stdPikachu on 2008-01-30
I ran into a thing on the live CD where my Nova-T wasn't properly recognised (no /dev/dvb/*); are you posting this from the live CD environment or from an installed system?

Also, do you have the Avermedia 771 card plugged in as well? I'd like to see the lspci entry for that, as I used to use one too and I don't recall "unclassified device" being a good sign...

---

### Post by Ubeast on 2008-01-30
stdPikachu, thanks for the reply, I'm posting from an installed system.

I just dropped my Avermedia 771 in and with both cards in a get an extra error on boot....

```
[   23.507318] PCI: Error while updating region 0000:01:07.1/0 (fdf00008 != f9f00008)
```

From lspci you can see it's the Avermedia card:

```
01:06.0 Non-VGA unclassified device: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: DViCO Corporation FusionHDTV DVB-T Plus
        Flags: medium devsel, IRQ 11
        Capabilities: <access denied>

01:06.2 Unclassified device [0080]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: DViCO Corporation Unknown device db11
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

01:07.0 Non-VGA unclassified device: Brooktree Corporation Bt878 Video Capture (rev 11)
        Subsystem: Avermedia Technologies Inc Unknown device 0371
        Flags: medium devsel, IRQ 3
        Memory at <unassigned> (32-bit, prefetchable) [disabled]
        Capabilities: <access denied>

01:07.1 Unclassified device [0080]: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Subsystem: Avermedia Technologies Inc Unknown device 0371
        Flags: medium devsel, IRQ 21
        Memory at fdf00000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>
```

I was obviously wrong about the Aver identifying as a Dvico, although it definately does in Mythtv-setup... that is when it works, which it isn't at the moment.

Here is a little more of kern.log, including the Avermedia card and some of the error lines that make me think it's irq related or something like that:

```
Jan 31 03:51:04 mythbuntu kernel: [   42.466791] bttv: driver version 0.9.17 loaded
Jan 31 03:51:04 mythbuntu kernel: [   42.466794] bttv: using 8 buffers with 2080k (520 pages) each for capture
Jan 31 03:51:04 mythbuntu kernel: [   42.466848] bttv: Bt8xx card found (0).
Jan 31 03:51:04 mythbuntu kernel: [   42.466859] PCI: Device 0000:01:07.0 not available because of resource 0 collisions
Jan 31 03:51:04 mythbuntu kernel: [   42.466861] bttv0: Can't enable device.
Jan 31 03:51:04 mythbuntu kernel: [   42.466864] bttv: probe of 0000:01:07.0 failed with error -5
Jan 31 03:51:04 mythbuntu kernel: [   42.476996] cx2388x v4l2 driver version 0.0.6 loaded
Jan 31 03:51:04 mythbuntu kernel: [   42.477031] PCI: Device 0000:01:06.0 not available because of resource 0 collisions
Jan 31 03:51:04 mythbuntu kernel: [   42.477036] cx8800: probe of 0000:01:06.0 failed with error -5
Jan 31 03:51:04 mythbuntu kernel: [   42.609521] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
Jan 31 03:51:04 mythbuntu kernel: [   42.609581] CORE cx88[0]: subsystem: 18ac:db11, board: DViCO FusionHDTV DVB-T Plus [card=21,autodetected]
Jan 31 03:51:04 mythbuntu kernel: [   42.609584] TV tuner 4 at 0x1fe, Radio tuner -1 at 0x1fe
Jan 31 03:51:04 mythbuntu kernel: [   42.616083] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 31 03:51:04 mythbuntu kernel: [   42.643020] lirc_dev: IR Remote Control driver registered, at major 61
Jan 31 03:51:04 mythbuntu kernel: [   42.647782] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Driver$
Jan 31 03:51:04 mythbuntu kernel: [   42.647786] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: Venky $
Jan 31 03:51:04 mythbuntu kernel: [   42.647810] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_p$
Jan 31 03:51:04 mythbuntu kernel: [   42.647816] lirc_dev: lirc_register_plugin: sample_rate: 0
Jan 31 03:51:04 mythbuntu kernel: [   42.647838] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_p$
Jan 31 03:51:04 mythbuntu kernel: [   42.647864] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/lirc/lirc_imon/lirc_imon.c: imon_p$
Jan 31 03:51:04 mythbuntu kernel: [   42.647874] usbcore: registered new interface driver lirc_imon
Jan 31 03:51:04 mythbuntu kernel: [   42.682277] Linux agpgart interface v0.102 (c) Dave Jones
Jan 31 03:51:04 mythbuntu kernel: [   42.683101] bt878: AUDIO driver version 0.0.0 loaded
Jan 31 03:51:04 mythbuntu kernel: [   42.694782] input: PC Speaker as /class/input/input6
Jan 31 03:51:04 mythbuntu kernel: [   42.812689] nvidia: module license 'NVIDIA' taints kernel.
Jan 31 03:51:04 mythbuntu kernel: [   43.075485] tveeprom 2-0050: Huh, no eeprom present (err=-121)?
Jan 31 03:51:04 mythbuntu kernel: [   43.081923] cx88[0]/2: cx2388x 8802 Driver Manager
Jan 31 03:51:04 mythbuntu kernel: [   43.081933] PCI: Enabling device 0000:01:06.2 (0000 -> 0002)
Jan 31 03:51:04 mythbuntu kernel: [   43.082124] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Jan 31 03:51:04 mythbuntu kernel: [   43.082130] ACPI: PCI Interrupt 0000:01:06.2[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20
Jan 31 03:51:04 mythbuntu kernel: [   43.082138] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 20, latency: 32, mmio: 0x40000000
Jan 31 03:51:04 mythbuntu kernel: [   43.082194] bt878: Bt878 AUDIO function found (0).
Jan 31 03:51:04 mythbuntu kernel: [   43.082202] PCI: Enabling device 0000:01:07.1 (0000 -> 0002)
Jan 31 03:51:04 mythbuntu kernel: [   43.082360] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
Jan 31 03:51:04 mythbuntu kernel: [   43.082364] ACPI: PCI Interrupt 0000:01:07.1[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 21
Jan 31 03:51:04 mythbuntu kernel: [   43.082377] bt878_probe: card id=[0x3711461], Unknown card.
Jan 31 03:51:04 mythbuntu kernel: [   43.082378] Exiting..
Jan 31 03:51:04 mythbuntu kernel: [   43.082382] ACPI: PCI interrupt for device 0000:01:07.1 disabled
Jan 31 03:51:04 mythbuntu kernel: [   43.082385] bt878: probe of 0000:01:07.1 failed with error -22
Jan 31 03:51:04 mythbuntu kernel: [   43.088341] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 20
Jan 31 03:51:04 mythbuntu kernel: [   43.088350] PCI: Setting latency timer of device 0000:05:00.0 to 64
Jan 31 03:51:04 mythbuntu kernel: [   43.088501] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
Jan 31 03:51:04 mythbuntu kernel: [   43.213764] cx2388x dvb driver version 0.0.6 loaded
Jan 31 03:51:04 mythbuntu kernel: [   43.213767] cx8802_register_driver() ->registering driver type=dvb access=shared
Jan 31 03:51:04 mythbuntu kernel: [   43.213771] CORE cx88[0]: subsystem: 18ac:db11, board: DViCO FusionHDTV DVB-T Plus [card=21]
Jan 31 03:51:04 mythbuntu kernel: [   43.213774] cx88[0]/2: cx2388x based dvb card
Jan 31 03:51:04 mythbuntu kernel: [   43.273292] mt352_read_register: readreg error (reg=127, ret==-121)
Jan 31 03:51:04 mythbuntu kernel: [   43.316750] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
Jan 31 03:51:04 mythbuntu kernel: [   43.316754] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
Jan 31 03:51:04 mythbuntu kernel: [   43.316769] PCI: Setting latency timer of device 0000:00:04.0 to 64
Jan 31 03:51:04 mythbuntu kernel: [   43.328098] zl10353_read_register: readreg error (reg=127, ret==-121)
Jan 31 03:51:04 mythbuntu kernel: [   43.328127] cx88[0]: frontend initialization failed
Jan 31 03:51:04 mythbuntu kernel: [   43.328129] cx8802_dvb_probe dvb_register failed err = -1
Jan 31 03:51:04 mythbuntu kernel: [   43.328131] cx8802_register_driver() ->probe failed err = -1
```

It doesn't look good but I really can't understand why considering how long and how well these cards have worked in the past.

Thanks again for trying to help out...

Jesse

---

### Post by stdPikachu on 2008-01-30
The capabilities "access denied" is a bit worrisome too, did you run lspci under sudo?

From the one time I had the error (ye olde b0rken mobo with a crummy VIA chipset), PCI region errors were generally the result of an IRQ conflict - can you post the complete output of `sudo lspci -vv` for our perusual?

---

### Post by Ubeast on 2008-01-30
Sorry lspci wasn't run undo sudo originally which would explain the 'access denied' message (I learn something everyday!), but here is a complete 'sudo lspci -vv'...

```
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
		Command: BaseUnitID=0 UnitCnt=15 MastHost- DefDir- DUL-
		Link Control 0: CFlE+ CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
		Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
		Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
		Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
		Revision ID: 1.03
		Link Frequency 0: 1.0GHz
		Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 0: 200MHz+ 300MHz+ 400MHz+ 500MHz+ 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
		Link Frequency 1: 200MHz
		Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
		Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
		Error Handling: PFlE+ OFlE+ PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
		Prefetchable memory behind bridge Upper: 00-00
		Bus Number: 00
	Capabilities: [e0] HyperTransport: MSI Mapping

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
	Subsystem: nVidia Corporation Unknown device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
	Subsystem: nVidia Corporation Unknown device cb84
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 4
	Region 0: I/O ports at fc00 [size=32]
	Region 4: I/O ports at 1c00 [size=64]
	Region 5: I/O ports at 1c40 [size=64]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: nVidia Corporation Unknown device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: nVidia Corporation Unknown device cb84
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at feb00000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: nVidia Corporation Unknown device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at f000 [size=256]
	Region 1: I/O ports at ec00 [size=256]
	Region 2: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: nVidia Corporation Unknown device cb84
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at e800 [size=16]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Unknown device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at 09f0 [size=8]
	Region 1: I/O ports at 0bf0 [size=4]
	Region 2: I/O ports at 0970 [size=8]
	Region 3: I/O ports at 0b70 [size=4]
	Region 4: I/O ports at d400 [size=16]
	Region 5: Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3) (prog-if 85 [Master SecO PriO])
	Subsystem: nVidia Corporation Unknown device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 09e0 [size=8]
	Region 1: I/O ports at 0be0 [size=4]
	Region 2: I/O ports at 0960 [size=8]
	Region 3: I/O ports at 0b60 [size=4]
	Region 4: I/O ports at c000 [size=16]
	Region 5: Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fdf00000-fdffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
	Subsystem: nVidia Corporation Unknown device cb84
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0 (250ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	Region 1: I/O ports at bc00 [size=8]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable+ DSel=0 DScale=0 PME-

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <4us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x2, ASPM L0s, Port 3
		Link: Latency L0s <512ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x4
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
		Slot: Number 8, PowerLimit 25.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Off, PwrInd On, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fdb00000-fdbfffff
	Prefetchable memory behind bridge: 00000000fda00000-00000000fdafffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <4us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 2
		Link: Latency L0s <512ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x4
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
		Slot: Number 4, PowerLimit 10.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Off, PwrInd On, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: fd900000-fd9fffff
	Prefetchable memory behind bridge: 00000000fd800000-00000000fd8fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <4us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 1
		Link: Latency L0s <512ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x8
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
		Slot: Number 2, PowerLimit 10.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Off, PwrInd On, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [58] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <4us
		Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s, Port 0
		Link: Latency L0s <512ns, L1 <4us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x16
		Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
		Slot: Number 1, PowerLimit 75.000000
		Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
		Slot: AttnInd Off, PwrInd On, Power-
		Root: Correctable- Non-Fatal- Fatal- PME-

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: [80] HyperTransport: Host or Secondary Interface
		!!! Possibly incomplete decoding
		Command: WarmRst+ DblEnd-
		Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0
		Link Config: MLWI=16bit MLWO=16bit LWI=16bit LWO=16bit
		Revision ID: 1.02

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

01:06.0 Non-VGA unclassified device: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: DViCO Corporation FusionHDTV DVB-T Plus
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
	Interrupt: pin A routed to IRQ 11
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:06.2 Unclassified device [0080]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: DViCO Corporation Unknown device db11
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
	Latency: 32 (1500ns min, 22000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:07.0 Non-VGA unclassified device: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: Avermedia Technologies Inc Unknown device 0371
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
	Interrupt: pin A routed to IRQ 3
	Region 0: Memory at <unassigned> (32-bit, prefetchable) [disabled]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:07.1 Unclassified device [0080]: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: Avermedia Technologies Inc Unknown device 0371
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at fdf00000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:09.0 PIC: VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [IO-APIC])
	Subsystem: DFI Inc Unknown device 1006
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
	Latency: 32 (8000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 5
	Region 1: I/O ports at ac00 [size=128]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1) (prog-if 00 [VGA])
	Subsystem: Giga-byte Technology Unknown device 3447
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at 6c00 [size=128]
	[virtual] Expansion ROM at fb000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [78] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
		Device: Latency L0s <512ns, L1 <4us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
		Link: Latency L0s <512ns, L1 <4us
		Link: ASPM Disabled RCB 128 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x16


```

---

### Post by stdPikachu on 2008-01-31
Unless you're running the latest nVidia chipset, I have no idea why you'd have so many "unknown device" lines in your lspci output which says to me something is awry with hardware somewhere. IIRC the CK804 is the nForce4 range, I've got two of those myself and they don't give me unknown anything. What's the motherboard/chipset?

You might also want to try `sudo lshw`, a slightly more verbose but less techy version of lspci. Not sure if it's installed by default.

---

### Post by Ubeast on 2008-02-01
> **stdPikachu said:**
> Unless you're running the latest nVidia chipset, I have no idea why you'd have so many "unknown device" lines in your lspci output which says to me something is awry with hardware somewhere. IIRC the CK804 is the nForce4 range, I've got two of those myself and they don't give me unknown anything. What's the motherboard/chipset?

You might also want to try `sudo lshw`, a slightly more verbose but less techy version of lspci. Not sure if it's installed by default.

Yes you're absolutely right, it is an NForce 4 chipset motherboard, and a few years old so it really shouldn't be a problem. It hasn't been in the past either... perhaps a rebuild is in order???

Here is the output of sudo lshw (which is installed by default btw):

```
mythbuntu
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: LP NF4 Series
       vendor: DFI Corp,LTD
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (04/06/2006)
          size: 128KB
          capacity: 448KB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.15.2
          slot: Socket 939
          size: 2412MHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc
        *-cache:0
             description: L1 cache
             physical id: b
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: d
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back
     *-cpu:1 DISABLED
          description: CPU
          vendor: Unknown
          physical id: 5
          bus info: cpu@1
          version: 15.15.2
          slot: Socket 939
          size: 2412MHz
          capacity: 3GHz
          clock: 201MHz
        *-cache:0
             description: L1 cache
             physical id: c
             slot: Internal Cache
             size: 128KB
             capacity: 128KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: e
             slot: External Cache
             size: 512KB
             capacity: 512KB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 512MB
             width: 64 bits
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: A3
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3 module=i2c_nforce2
     *-usb:0
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: CK804 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
        *-ide:0
             description: IDE Channel 0
             physical id: 0
             bus info: ide@0
             logical name: ide0
             clock: 66MHz
           *-cdrom
                description: DVD-RAM writer
                product: HL-DT-ST DVDRAM GSA-4167B
                physical id: 0
                bus info: ide@0.0
                logical name: /dev/hda
                version: DL12
                serial: 4225FE65D761
                capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: mode=udma2 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/hda
        *-ide:1
             description: IDE Channel 1
             physical id: 1
             bus info: ide@1
             logical name: ide1
             clock: 66MHz
           *-disk
                description: ATA Disk
                product: WDC WD1200JB-00GVA0
                vendor: Western Digital
                physical id: 0
                bus info: ide@1.0
                logical name: /dev/hdc
                version: 08.02D08
                serial: WD-WCALA1771273
                size: 111GB
                capacity: 111GB
                capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                configuration: mode=udma5 smart=on
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: ide@1.0,1
                   logical name: /dev/hdc1
                   capacity: 18GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: ide@1.0,2
                   logical name: /dev/hdc2
                   capacity: 1953MB
                   capabilities: primary nofs
              *-volume:2
                   description: Linux LVM Physical Volume partition
                   physical id: 3
                   bus info: ide@1.0,3
                   logical name: /dev/hdc3
                   serial: EKv1Ke-SwIF-U0ZK-461U-6sPx-9wpJ-upnEMC
                   size: 91GB
                   capacity: 91GB
                   capabilities: primary multi lvm2
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: scsi0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
        *-disk
             description: SCSI Disk
             product: WDC WD3200KS-00P
             vendor: ATA
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 21.0
             serial: WD-WCAPD2219412
             size: 298GB
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5
           *-volume
                description: Linux LVM Physical Volume partition
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                serial: hoOhM8-EktN-2DJM-7h3j-Nzp1-tsLy-XmI9Yq
                size: 298GB
                capacity: 298GB
                capabilities: primary multi lvm2
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
        *-generic:0 UNCLAIMED
             description: Non-VGA unclassified device
             product: CX23880/1/2/3 PCI Video and Audio Decoder
             vendor: Conexant
             physical id: 6
             bus info: pci@0000:01:06.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm cap_list
             configuration: latency=32 maxlatency=51 mingnt=20
        *-generic:1
             description: Unclassified device
             product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
             vendor: Conexant
             physical id: 6.2
             bus info: pci@0000:01:06.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=cx88-mpeg driver manager latency=32 maxlatency=88 mingnt=6 module=cx8802
        *-generic:2 UNCLAIMED
             description: Non-VGA unclassified device
             product: Bt878 Video Capture
             vendor: Brooktree Corporation
             physical id: 7
             bus info: pci@0000:01:07.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm cap_list
             configuration: latency=32 maxlatency=40 mingnt=16
        *-generic:3 UNCLAIMED
             description: Unclassified device
             product: Bt878 Audio Capture
             vendor: Brooktree Corporation
             physical id: 7.1
             bus info: pci@0000:01:07.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm cap_list
             configuration: latency=32 maxlatency=251 mingnt=4
        *-system UNCLAIMED
             description: PIC
             product: IEEE 1394 Host Controller
             vendor: VIA Technologies, Inc.
             physical id: 9
             bus info: pci@0000:01:09.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm io-apic bus_master cap_list
             configuration: latency=32 maxlatency=32
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a3
          serial: 00:01:29:d2:ec:53
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=192.168.1.243 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display
             description: VGA compatible controller
             product: GeForce 8600 GT
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:05:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga bus_master cap_list
             configuration: driver=nvidia latency=0 module=nvidia
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp

```

and with the -businfo switch:

```
Bus info          Device     Class       Description
====================================================
                             system      Desktop Computer
                             bus         LP NF4 Series
                             memory      128KB BIOS
cpu@0                        processor   AMD Athlon(tm) 64 Processor 3800+
                             memory      128KB L1 cache
                             memory      512KB L2 cache
cpu@1                        processor   CPU
                             memory      128KB L1 cache
                             memory      512KB L2 cache
                             memory      1GB System Memory
                             memory      512MB DIMM
                             memory      512MB DIMM
                             memory      DIMM [empty]
                             memory      DIMM [empty]
pci@0000:00:00.0             memory      CK804 Memory Controller
pci@0000:00:01.0             bridge      CK804 ISA Bridge
pci@0000:00:01.1             bus         CK804 SMBus
pci@0000:00:02.0             bus         CK804 USB Controller
pci@0000:00:02.1             bus         CK804 USB Controller
pci@0000:00:04.0             multimedia  CK804 AC'97 Audio Controller
pci@0000:00:06.0             storage     CK804 IDE
ide@0             ide0       bus         IDE Channel 0
ide@0.0           /dev/hda   disk        HL-DT-ST DVDRAM GSA-4167B
                  /dev/hda   disk        
ide@1             ide1       bus         IDE Channel 1
ide@1.0           /dev/hdc   disk        111GB WDC WD1200JB-00GVA0
ide@1.0,1         /dev/hdc1  volume      18GB Linux filesystem partition
ide@1.0,2         /dev/hdc2  volume      1953MB Linux swap / Solaris partition
ide@1.0,3         /dev/hdc3  volume      91GB Linux LVM Physical Volume partition
pci@0000:00:07.0  scsi0      storage     CK804 Serial ATA Controller
scsi@0:0.0.0      /dev/sda   disk        298GB WDC WD3200KS-00P
scsi@0:0.0.0,1    /dev/sda1  volume      298GB Linux LVM Physical Volume partition
pci@0000:00:08.0             storage     CK804 Serial ATA Controller
pci@0000:00:09.0             bridge      CK804 PCI Bridge
pci@0000:01:06.0             generic     CX23880/1/2/3 PCI Video and Audio Decoder
pci@0000:01:06.2             generic     CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
pci@0000:01:07.0             generic     Bt878 Video Capture
pci@0000:01:07.1             generic     Bt878 Audio Capture
pci@0000:01:09.0             system      IEEE 1394 Host Controller
pci@0000:00:0a.0  eth0       bridge      CK804 Ethernet Controller
pci@0000:00:0b.0             bridge      CK804 PCIE Bridge
pci@0000:00:0c.0             bridge      CK804 PCIE Bridge
pci@0000:00:0d.0             bridge      CK804 PCIE Bridge
pci@0000:00:0e.0             bridge      CK804 PCIE Bridge
pci@0000:05:00.0             display     GeForce 8600 GT
pci@0000:00:18.0             bridge      K8 [Athlon64/Opteron] HyperTransport Technology Configuration
pci@0000:00:18.1             bridge      K8 [Athlon64/Opteron] Address Map
pci@0000:00:18.2             bridge      K8 [Athlon64/Opteron] DRAM Controller
pci@0000:00:18.3             bridge      K8 [Athlon64/Opteron] Miscellaneous Control

```

---

### Post by ozybushwalker on 2008-02-02
There are a few clues that suggest there is something wrong with your cards OR you haven't seated them correctly in the PCI slots.

I compared your device dsecriptions from lspci and friends with that of my system which has a Leadtek DTV2000H digital TV card which appears to use chips from the same family of one of your cards.

Here's part of the lshw -businfo output
> 
pci@0000:00:05.0             multimedia  CX23880/1/2/3 PCI Video and Audio Decod
pci@0000:00:05.1             multimedia  CX23880/1/2/3 PCI Video and Audio Decod
pci@0000:00:05.2             multimedia  CX23880/1/2/3 PCI Video and Audio Decod


Each PCI device has a "configuration area" which contains codes for the type of device (e.g. multimedia, network, bridge  display etc). I would expect your CX23880 devices to be "multimedia" rather than "generic" or "Non-VGA unclassified".

I don't know what the following means, but there is only one bit different between thw two values.
> 
[   23.507318] PCI: Error while updating region 0000:01:07.1/0 (fdf00008 != f9f00008)


The resource conflict message suggests the BIOS has apparently assigned non-distinct address ranges to different PCI devices. This shouldn't happen but could if the base address of the assignments to two different devices differed by a single bit and that bit was read unreliably.

I don't know if your dusting resulted in some damage to your cards OR the PCB fingers picked up some "foreign" material that prevents the slot fingers making effective contact with the card.

I suggest you take the cadrs out, give the PCB fingers that go into the slot close visiual inspection for foreign material then put the cards back, taking special care that the card is fully inserted into the slot. You can apply a fair bit of pressure which is sometimes needed  I have found the end of the card furtherest from the motherboard edge sometimes sits up a bit from the motherboard connector and doesn't make good contact.

You should be able to plug the cards in any avaialble slot. It would be worth trying one card at a time in all the available slots until you find a slot that works. its possible (especially if the slots have been used recently) that some foreign material may have fallen into one or more slots preventing the cards from making good contact with the slot connector.

---

### Post by Ubeast on 2008-02-03
G'day ozybushwalker,

Thanks for the extra info mate, I'll check for crap in the pci slots, but the board was pretty clean, and I doubt I damaged the tuner cards during the rebuild - I'm actually fairly fastidious when it comes to computer care. I've only ever destroyed one card in 15 years of playing with PCs and that was due to a insidous slow seep in a water cooled computer I had :). To be honest I don't know why the orig motherboard stopped playing the game... still need to investigate.

I have a third tuner card, another DVICO that I can try... that will rule out damage as it has sat dormant for a year so it should still be in fine condition. I suspect there is something set in the bios of this new (replacement) motherboard that is different enough to the old (now dead) motherboard that it is stopping the PCI tuner cards from working - despite the fact two mobos are practically identical.

I could just go for the reinstall and hope for the best, but I'm sure there is a more elegant solution (bios or software) and I'd like to try and find it first.

I really appreciate all the help you guys are trying to give... many thanks - keep it coming.

---

### Post by Ubeast on 2008-02-12
Well after a weeks of fault finding every single component on the motherboard, and even trying another motherboard from my main machine (a DFI Lanparty UT NF4 SLI-DR Expert) which functioned correctly... I finally found the problem.

The replacement motherboard has faulty PCI slots. Worse still, the guy that sold me the motherboard knew of the problem (I checked his back posts and he was complaining of the same thing over a year ago) and sold it to me anyway. Given he lives 20 minutes from my house, we're are going to be having serious words.

On a positive note, I now have a (3rd) working motherboard in place and Mythbuntu is up and running just fine.

Thanks to everyone who tried to help... at the very least I learnt a bunch of new things, so thanks guys.

---

