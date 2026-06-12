---
title: "Help seting up AverMedia DVB Tuner Card in Mythbuntu 10.10"
date: 2011-03-19
forum: Mythbuntu
---

### Post by sparafucile17 on 2011-03-19
Hello,

I have previosly setup and got Mythbunut 10.0 on my HTPC.  So far,  have got the following running:

[LIST=1]
[*]Hulu integrated
[*]DVD ripping
[*]Media Library Playback (from ripped DVDs)
[/LIST]
At the time on install I had not yet received my DVB tuner card, so it was not present at the time of install.  So now I am trying to install the hardware and just get live TV running for now.  I am using an AverMedia Duet DVB tuiner and I am connecting to WoW TV service in the U.S.

I am really at a loss or what to do.  I went into the backed setup and tried using "[B]DVB DTV TV-Card (v3.x)", but no where on the setup screen do  see a spot where I would tell it to use the AverMedia PCIe card.  In looking at other forum posts I see that the tool lspci seems to be helpful and this is what it output for me:

[/B]> 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
03:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

[B]So what should I do?  I  just stuck the card in 30 minutes ago and  booted up the HTPC and haven't a clue what to do next.  Any help is greatly appreciated.  (i.e. Help I'm stuck)

- Jeff
[/B]

---

### Post by sparafucile17 on 2011-03-19
OK,  after a little bit more debugging, I have found my device.  I just had to type lspci -vv to finally see teh AverMedia label.  It looks like this:

> 
03:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 01)
    Subsystem: Avermedia Technologies Inc Device 1e55
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
Still not sure what to do next though.  I am thinking that I need to install the driver maybe?  But where I would get this I haven't a clue.

- Jeff

---

### Post by sparafucile17 on 2011-03-22
Hi, I'm bumping this thread to hopefully gain some more attention :)

I just found a list of supported tuner cards and the AverMedia Duet is not on the list :(

[http://www.mythtv.org/wiki/Digital_Tuner_Cards](http://www.mythtv.org/wiki/Digital_Tuner_Cards)


Should I just return my card and buy one of the listed cards instead?  If I do, should it just be plug-n-play afterwards?  I don't want to go through the effort of returning the card if I just needed to play with some config files to get it to work.

- Jeff

---

