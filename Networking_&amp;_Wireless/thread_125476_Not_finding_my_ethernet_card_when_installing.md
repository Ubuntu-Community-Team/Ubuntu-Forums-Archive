---
title: "Not finding my ethernet card when installing"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by krishnanv on 2006-02-04
I am facing a problem with my PC. I have an ADSL net connection. But Ubuntu 5.10 could not detect my ethernet card on installation (it detected a firewire ethernet card which I don't have) and now I am not able to connect to net.
Following is the output of lspci command:
0000:00:00.0 Host bridge: Intel Corp. 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82850 850 (Tehama) Chipset AGP Bridge (rev 02)

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 04)

0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 04)

0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 04)

0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 04)

0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 04)

0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)

0000:02:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)

0000:02:0c.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)

I am new to ubuntu linux.
Thanks in advance.

Krishnan

---

### Post by joselin on 2006-02-04
I had the same troubles with one of my laptops (and IBM), and i could solve it adding acpi=off to the kernel.

On /boot/grub/menu.lst: 
```

/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash acpi=off

```

Then for appliyin the changes do:
```

# /sbin/grub-install /dev/hda

```

Good luck.

---

### Post by bscbrit on 2006-02-04
[https://wiki.ubuntu.com/NetworkCards](https://wiki.ubuntu.com/NetworkCards)

Good luck.

---

### Post by krishnanv on 2006-02-04
Thanks joselin for the quick response. I tried adding the same in menu.lst and ran the install command. But my administration> networking menu still does not show the card. How do I connect to the internet using my ethernet card. Folllowing is the ver verbose description of lspci command. I hope somebody can help me.

0000:00:00.0 Host bridge: Intel Corp. 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 82850 850 (Tehama) Chipset AGP Bridge (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: fc900000-fe9fffff
        Prefetchable memory behind bridge: f0600000-f46fffff
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 04) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fea00000-feafffff
        Prefetchable memory behind bridge: f4700000-f47fffff
        BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

0000:00:1f.0 ISA bridge: Intel Corp. 82801BA ISA Bridge (LPC) (rev 04)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:1f.1 IDE interface: Intel Corp. 82801BA IDE U100 (rev 04) (prog-if 80 [Master])
        Subsystem: Intel Corp.: Unknown device 4732
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 4: I/O ports at ffa0 [size=16]

0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 04) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4732
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 5
        Region 4: I/O ports at ef40 [size=32]

0000:00:1f.3 SMBus: Intel Corp. 82801BA/BAM SMBus (rev 04)
        Subsystem: Intel Corp.: Unknown device 4732
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 10
        Region 4: I/O ports at efa0 [size=16]

0000:00:1f.4 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #2) (rev 04) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4732
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 9
        Region 4: I/O ports at ef80 [size=32]

0000:01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at f2000000 (32-bit, prefetchable) [size=32M]
        Expansion ROM at fe9f0000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:02:0a.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
        Subsystem: Conexant Dynalink 56PMi
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 3
        Region 0: Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
        Region 1: I/O ports at dff0 [size=8]
        Capabilities: <available only to root>

0000:02:0c.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI128
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort+ <MAbort+ >SERR- <PERR-
        Latency: 32 (3000ns min, 32000ns max)
        Interrupt: pin A routed to IRQ 10
        Region 0: I/O ports at df00 [size=64]
        Capabilities: <available only to root>



[QUOTE=joselin]I had the same troubles with one of my laptops (and IBM), and i could solve it adding acpi=off to the kernel.

On /boot/grub/menu.lst: 
```

/boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash acpi=off

```

Then for appliyin the changes do:
```

# /sbin/grub-install /dev/hda

```

Good luck.[/QUOTE]

---

### Post by bscbrit on 2006-02-04
What make and model is your PCI card?

EDIT:  Apologies for the useless link a post or two back!  Not the one that I thought it was.

---

### Post by krishnanv on 2006-02-15
Following is the network device:
D-Link USB Remote NDIS Network Device

Regards,
Krishnan

[QUOTE=bscbrit]What make and model is your PCI card?

EDIT:  Apologies for the useless link a post or two back!  Not the one that I thought it was.[/QUOTE]

---

