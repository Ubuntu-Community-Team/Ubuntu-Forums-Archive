---
title: "Sound problems."
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by coolen on 2007-12-13
Okay, here's the low-down:

A couple of weeks ago, I had to install XP for a LAN party. Party went bust, but I decided to use the opportunity to play some games which didn't run under Wine.
Well, I hate resetting, so I was in XP for a couple of weeks. I got sick of it and sought refuge with Ubuntu the other day, only to discover that, amongst the copious amount of win, sound was not working.

My first thought was breakage, but I'd not done a kernel update.

My current thought is a permissions problem. Here's the relevant section of lspci -vv: 

```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Giga-byte Technology Unknown device a002
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at f5100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

Here's suo lspci -vv:

```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Giga-byte Technology Unknown device a002
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at f5100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
                Masking: 00000000  Pending: 00000000
        Capabilities: [6c] HyperTransport: MSI Mapping
```

I tried a chmod on both /dev/dsp and /dev/audio, but to no avail. I also tried modprobe snd-intel8x0, which is what I think it should be (my specific card wasn't listed, but this is what every other nVidia card uses. I also tried snd-intel8x0m.

It always worked before. I checked to see if I'd eroneously booted the 386 kernel, but I was using generic.

Little help?

---

### Post by deadgobby on 2007-12-13
Just a silly question, just a silly one. A little KISS method here. Did you disable the on board sound device in BIOS?

---

### Post by coolen on 2007-12-13
No. I haven't touched the BIOS settings since the XP install, and sound works fine in Windows.

---

### Post by MachineBucket on 2007-12-13
I have a similar problem with my laptop. It's a Gateway MX7515. I dual boot with Windows and I have never had a problem with sound in Windows either. Sometimes when I boot into Ubuntu I have no sound at all, and it takes anywhere between 1-6 reboots to get it working again.

Here is the output of lspci
```
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
```

I've had this problem since 6.06, I just never got around to fixing it. Then I stopped using Ubuntu until Gutsy released. So far today I've fixed the boot splash screen bug and desktop effects, now I'm on to the next problem! :twisted:

Hopefully a fix will pertain to both the OP's problem and mine too.

---

### Post by coolen on 2007-12-13
Could you run lspci -vv? I think the <access denied> part may be pertinent (although I tried playing a song through Totem as root and still got nothing...).
I've never had a problem with sound using the generic kernel before. It was one of the things I so very loved about Ubuntu.

That command was with two v's, not a w. Double verbosity.

---

### Post by MachineBucket on 2007-12-13
I just searched SB400 in the forums and found a thread on my particular problem. The on board modem shares the same chip as the soundcard. Ubuntu was sometimes loading the modem driver as my primary sound device, so I just blacklisted it. It works fine now.

Have you tried using lsmod to see what drivers you have loaded for your soundcard?

---

### Post by coolen on 2007-12-15
According to lsmod, the driver for my sound card was not loaded. I loaded it, and still nothing.

I don't understand why it's cut out on me now. I've tried searching for my sound card, but imagine what I got when I searched for Nvidia...

---

