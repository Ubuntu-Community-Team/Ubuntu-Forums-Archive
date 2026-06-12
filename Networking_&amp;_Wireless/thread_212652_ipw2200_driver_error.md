---
title: "ipw2200 driver error?"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by mech7 on 2006-07-10
I am getting this error when i want to install it does anybody know how to solve it ?

> sudo make install
/home/chris/ipw2200-1.1.3/ipw2200.c: In function ‘ipw_pci_probe’:
/home/chris/ipw2200-1.1.3/ipw2200.c:12273: error: ‘struct ieee80211_device’ has no member named ‘is_qos_active’
make[2]: *** [/home/chris/ipw2200-1.1.3/ipw2200.o] Error 1
make[1]: *** [_module_/home/chris/ipw2200-1.1.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-686'
make: *** [modules] Error 2
chris@chris:~/ipw2200-1.1.3$ sudo make install
mkdir -p /home/chris/ipw2200-1.1.3/tmp/.tmp_versions
cp /lib/modules/2.6.15-23-686/net/ieee80211/.tmp_versions/*.mod /home/chris/ipw2200-1.1.3/tmp/.tmp_versions
make -C /lib/modules/2.6.15-23-686/build M=/home/chris/ipw2200-1.1.3 MODVERDIR=/home/chris/ipw2200-1.1.3/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-23-686'
 CC [M]  /home/chris/ipw2200-1.1.3/ipw2200.o
/home/chris/ipw2200-1.1.3/ipw2200.c: In function ‘ipw_pci_probe’:
/home/chris/ipw2200-1.1.3/ipw2200.c:12273: error: ‘struct ieee80211_device’ has no member named ‘is_qos_active’
make[2]: *** [/home/chris/ipw2200-1.1.3/ipw2200.o] Error 1
make[1]: *** [_module_/home/chris/ipw2200-1.1.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-23-686'
make: *** [modules] Error 2


---

### Post by Athropos on 2006-07-10
> **mech7 said:**
> I am getting this error when i want to install it does anybody know how to solve it ?

Are you sure you have to compile and install it yourself? I myself have a Dell laptop with the same chipset, and it is automatically recognized by the kernel in Dapper (this wasn't the case in Breezy). I even got access to Internet during my Dapper install...

---

### Post by mech7 on 2006-07-10
yes i am positive.. only my normal lan card works.. i have it attached now to netgear game adapter from my xbox so that i can still go on the internet... the intel card really does not work on my acer travelmate 4102 WLM

---

### Post by awaldram on 2006-07-10
> **mech7 said:**
> yes i am positive.. only my normal lan card works.. i have it attached now to netgear game adapter from my xbox so that i can still go on the internet... the intel card really does not work on my acer travelmate 4102 WLM

Think You'll find you just need to 'switch it on' with acerhk

[http://www2.informatik.hu-berlin.de/~tauber/acerhk/](http://www2.informatik.hu-berlin.de/~tauber/acerhk/)

---

### Post by mech7 on 2006-07-10
Ok i reinstalled it and did it again.. new drivers are running new firmware new eee8021 etc..  only now i don't even have interent rhtough my regular lan card ?
Also I have tried the hotkey as i think this is indeed the problem but it does not work :( As i don't see any lights burning...

[[IMG]http://img45.imageshack.us/img45/9941/screenshot3gd.png[/IMG]](http://imageshack.us)



> 
chris@acerChris:~$ dmesg | grep ipw
[4294687.917000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.3dmprq
[4294687.917000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294688.074000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294688.295000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
chris@acerChris:~$ lspci -vv
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0

        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 0x08 (32 bytes)
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: c8100000-c81fffff
        Prefetchable memory behind bridge: d0000000-d7ffffff
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 0x08 (32 bytes)
        Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <available only to root>

0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04) (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 0x08 (32 bytes)
        Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <available only to root>

0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04) (prog-if 00 [Normal decode])
        Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 0x08 (32 bytes)
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=0
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 50
        Region 4: I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 58
        Region 4: I/O ports at 1820 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 185
        Region 4: I/O ports at 1840 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 169
        Region 4: I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 50
        Region 0: Memory at c8000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=06, subordinate=08, sec-latency=216
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: c8200000-c82fffff
        Prefetchable memory behind bridge: 0000000030000000-0000000031f00000
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: <available only to root>

0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 177
        Region 0: I/O ports at 1c00 [size=256]
        Region 1: I/O ports at 1880 [size=64]
        Region 2: Memory at c8000800 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at c8000400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 233
        Region 0: I/O ports at 2400 [size=256]
        Region 1: I/O ports at 2000 [size=128]
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 185
        Region 0: I/O ports at <unassigned>
        Region 1: I/O ports at <unassigned>
        Region 2: I/O ports at <unassigned>
        Region 3: I/O ports at <unassigned>
        Region 4: I/O ports at 18c0 [size=16]

0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 11
        Region 4: I/O ports at 20a0 [size=32]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 169
        Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at 3000 [size=256]
        Region 2: Memory at c8100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at c8120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 185
        Region 0: Memory at c8208000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=08, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 32000000-33fff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

0000:06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (750ns min, 1000ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 185
        Region 0: Memory at c8209000 (32-bit, non-prefetchable) [size=2K]
        Region 1: Memory at c8200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at c8204000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

0000:06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
        Subsystem: Intel Corporation: Unknown device 2701
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (750ns min, 6000ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 177
        Region 0: Memory at c820a000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:06:08.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0066
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Interrupt: pin A routed to IRQ 169
        Region 0: Memory at c8206000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

chris@acerChris:~$


---

### Post by mech7 on 2006-07-10
When i do..

8. Try loading the module with:
	insmod/modprobe acerhk
If it succeeds - congratulations! If you have procfs enabled, you can try the
following to test the driver:


It says no file or directory 0_o is something missing frim this command ?

---

### Post by mech7 on 2006-07-10
the modules does seem to be loaded? :(

> chris@acerChris:~$ lsmod
Module                  Size  Used by
acerhk                 29820  0
ipv6                  286912  20

---

### Post by mech7 on 2006-07-10
It tells me this :(

> chris@acerChris:~$ echo 1 > /proc/driver/acerhk/wirelessled
bash: /proc/driver/acerhk/wirelessled: No such file or directory


---

### Post by mech7 on 2006-07-11
:cry: Nobody knows how to do this ?

---

### Post by stupidkid on 2006-07-11
Dapper should have built in support for this card. It worked automatically on my Dell Latitude. The module name is ipw2200 I believe.

Can you post your whole lsmod and iwconfig?

---

