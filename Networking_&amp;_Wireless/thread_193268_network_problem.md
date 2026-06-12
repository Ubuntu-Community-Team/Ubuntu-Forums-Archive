---
title: "network problem"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by skale on 2006-06-09
I have a "Dell Truemobile 1180 wireless USB adapter"

I believe I also have an ethernet card on the computer, but I've never used it. I    did the whole wireless troubleshooting guide verbatim and it didn't help much. 
when I do "lshw -C network", 
it brings up two ethernet controllers , eth0 and wlan. eth0 looks good, but I don't have a cable or an outlet in my room. wlan0 is disabled, kinda like the laptop thing in 4.2.5 in the guide. I don't have a laptop.
I also searched the forum, but didn't find anything. But, I didn't know what to look for either. If there is a thread like this already, could you direct me top it?
 :)

---

### Post by ns2048 on 2006-06-09
Seems you have a Broadcom 43xx chipset in your card -- which doesn't have a native Linux device driver.

Take a look at [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

--ns2048

---

### Post by skale on 2006-06-10
[QUOTE=ns2048]Seems you have a Broadcom 43xx chipset in your card -- which doesn't have a native Linux device driver.

Take a look at [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx)

--ns2048[/QUOTE]
I don't. I checked, and then tried it out anyway. No luck. 

I downloaded the driver for the truemobile 1180 USB from the dell.com website. then I do the "sudo ndiswrapper" command, and it says:
"installing r56541.exe
"couldn't copy /home/...  .../R56541.exe at /usr/sbin/ndiswrapper line 135"

Reads like gibberish to me. I have no Idea what to do, except go back to XP. I went through every guide I could get my hands on. Maybe I need a new card, but Id rather not get a new one, being short of cash. 

I'm at a loss really. Also, > 4.2.5. Driver looks ok, device disabled

    *

      Newer laptops come with features to disable the wireless radio to save battery when not in use. Usually this is switched by a FN+Fx key combo or specific button for the purpose. It is possible driver and everything is ok but the wireless device is in the disabled state and can't be used. Using the designated key(s) in linux sometimes does not work.

      Usually this is apparent by running the lshw command you see *-network:1 DISABLED or if you run the iwconfig command you see eth1      NOT READY!. 
applies to me. Which is odd, since I'm on a desktop.

edit:
ndiswrapper -l reads"
"r56541.exe    invalid driver!"

---

### Post by ns2048 on 2006-06-11
Running ndiswrapper against the '.EXE' won't work. You'll have to

* Extract the driver files from the .EXE into a folder, using Windows
* Copy this folder to your Linux partition (or somewhere where Ubuntu can access it)
* Look for an '.INF' file in this folder
* Run 'ndiswrapper -i PATH_TO_INF_FILE', to install the Windows driver

If all goes well, running 'ndiswrapper -l' should show that the driver is loaded and the network adapter is present. You can also check '/var/log/dmesg' to see if the network adapter was detected correctly.

To load ndiswrapper during system bootup, add the line 'alias wlan0 ndiswrapper' to '/etc/modprobe.d/aliases'

--ns2048

---

### Post by skale on 2006-06-11
There is no .inf file.

There is:
.cab
.EX_
.exe
.inx
.hdr
.dll
.ini

---

### Post by ns2048 on 2006-06-12
I suspect the '.INF' file is inside the '.cab' archive. Can you post the output of 'lspci -vv' and 'lspci -n'?

--ns2048

---

### Post by skale on 2006-06-12
> sameer@Sameer:~$ sudo lspci -n
Password:
0000:00:00.0 0600: 8086:2570 (rev 02)
0000:00:01.0 0604: 8086:2571 (rev 02)
0000:00:1d.0 0c03: 8086:24d2 (rev 02)
0000:00:1d.1 0c03: 8086:24d4 (rev 02)
0000:00:1d.2 0c03: 8086:24d7 (rev 02)
0000:00:1d.3 0c03: 8086:24de (rev 02)
0000:00:1d.7 0c03: 8086:24dd (rev 02)
0000:00:1e.0 0604: 8086:244e (rev c2)
0000:00:1f.0 0601: 8086:24d0 (rev 02)
0000:00:1f.1 0101: 8086:24db (rev 02)
0000:00:1f.2 0101: 8086:24d1 (rev 02)
0000:00:1f.3 0c05: 8086:24d3 (rev 02)
0000:00:1f.5 0401: 8086:24d5 (rev 02)
0000:01:00.0 0300: 10de:0181 (rev a2)
0000:02:01.0 0703: 14e4:4212 (rev 02)
0000:02:08.0 0200: 8086:1050 (rev 02)

> sameer@Sameer:~$ sudo lspci -vv
\0000:00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Dell: Unknown device 0155
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort+ <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [e4] #09 [2106]
        Capabilities: [a0] AGP version 3.0
                Status: RQ=32 Iso- ArqSz=2 Cal=2 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=2 SBA+ AGP- GART64- 64bit- FW- Rate=<none>

0000:00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: fd000000-feafffff
        Prefetchable memory behind bridge: f0000000-f7ffffff
        BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-

0000:00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0155
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 185
        Region 4: I/O ports at ff80 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0155
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 193
        Region 4: I/O ports at ff60 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0155
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 177
        Region 4: I/O ports at ff40 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0155
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 185
        Region 4: I/O ports at ff20 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 0155
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 201
        Region 0: Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] #0a [20a0]

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fcf00000-fcffffff
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-

0000:00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell: Unknown device 0155
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 177
        Region 0: I/O ports at <ignored>
        Region 1: I/O ports at <ignored>
        Region 2: I/O ports at <ignored>
        Region 3: I/O ports at <ignored>
        Region 4: I/O ports at ffa0 [size=16]
        Region 5: Memory at febffc00 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Dell: Unknown device 0155
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 177
        Region 0: I/O ports at fe00 [size=8]
        Region 1: I/O ports at fe10 [size=4]
        Region 2: I/O ports at fe20 [size=8]
        Region 3: I/O ports at fe30 [size=4]
        Region 4: I/O ports at fea0 [size=16]

0000:00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: Dell: Unknown device 0155
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 3
        Region 4: I/O ports at eda0 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Dell: Unknown device 0155
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 209
        Region 0: I/O ports at ee00 [size=256]
        Region 1: I/O ports at edc0 [size=64]
        Region 2: Memory at febffa00 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at febff900 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation: Unknown device 01b6
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 185
        Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at fea00000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [44] AGP version 3.0
                Status: RQ=32 Iso- ArqSz=0 Cal=3 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

0000:02:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02) (prog-if 00 [Generic])
        Subsystem: Dell: Unknown device 0001
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 169
        Region 0: Memory at fcffe000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at df30 [size=16]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

0000:02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
        Subsystem: Dell: Unknown device 0155
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (2000ns min, 14000ns max), Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 217
        Region 0: Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at df40 [size=64]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-



Here they are. Hope they help. I came home just now so I'll try and figure out the .cab stuff. Thanks!:KS

edit: 

I downloaded a cab extractor thingy and found a NETDELUS.inf. Ill try it in a bit.

---

### Post by skale on 2006-06-13
I extracted the cab file and moved the whole thing to the Ubuntu computer. now there are some other issues, as well, surrounding the depmod and nodprobe commands. The installation went as expected until then, when I did the ifconfig and iwconfig there was no wireless.

:confused:

---

