---
title: "Help requested installin tenda w322u ubuntu 11.4"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by Paul28799 on 2011-08-06
I am new to ubuntu and I am having a problem trying to get my new Tenda W322U wireless N usb to work on ubuntu 11.04. I have tried to follow instructions listed by others on the net but it appears still not to work.

I have tested it in windows...and it works flawlessly....but I really want to use it with ubuntu.

I have gone into terminal and it was shown as connected to the laptop but the built in wireless g seems to over ride the device and connects auto.

Could someone please help me and provide some detailed instructions as to how this small issue could be resolved.  Any help would be greatly appreciated.

Thanks for taking the time to read this post.

Paul

---

### Post by lkjoel on 2011-08-06
Could you give me the output of these Terminal commands?
```
uname -a
lspci -vvnn
ifconfig
iwconfig
nm-tool

```

---

### Post by Paul28799 on 2011-08-07
Hi the info as follows:

dell@dell-Latitude-D510:~$ uname -a
Linux dell-Latitude-D510 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux
dell@dell-Latitude-D510:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
02:01.2 FireWire (IEEE 1394): Texas Instruments Device 8037
02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
03:00.0 SATA controller: Initio Corporation INI-1623 PCI SATA-II Controller (rev 02)
dell@dell-Latitude-D510:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:c0:17:ca  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:89:c3:de  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe89:c3de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2737 errors:1 dropped:1 overruns:0 frame:0
          TX packets:2550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2978675 (2.9 MB)  TX bytes:457582 (457.5 KB)
          Interrupt:17 Base address:0x6000 Memory:dfdf9000-dfdf9fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

dell@dell-Latitude-D510:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"ASUS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 20:CF:30:B7:C3:D4   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=90/100  Signal level=-39 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

---

### Post by Paul28799 on 2011-08-07
And the rest:

dell@dell-Latitude-D510:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:14:22:C0:17:CA

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1  [Auto ASUS] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             connected
  Default:           yes
  HW Address:        00:13:CE:89:C3:grin:E

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    NEILTHOMSON-Wireless: Infra, 00:22:3F:8C:BC:42, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    *ASUS:           Infra, 20:CF:30:B7:C3:grin:4, Freq 2437 MHz, Rate 54 Mb/s, Strength 93 WPA WPA2
    ASUS:            Infra, 20:CF:30:B7:C3:grin:5, Freq 5180 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2
    BTFON:           Infra, 0A:8B:5D:8F:9C:82, Freq 2462 MHz, Rate 54 Mb/s, Strength 68
    BTOpenzone:      Infra, 06:8B:5D:8F:9C:82, Freq 2462 MHz, Rate 54 Mb/s, Strength 68
    virginmedia6195275: Infra, C0:3F:0E:C0:55:9F, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    SKY88131:        Infra, 5C:grin:9:98:C2:89:8C, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    sod:             Infra, 00:26:5A:1E:BB:6E, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Teresa-PC-Wireless: Infra, 00:26:F2:4D:82:C2, Freq 2442 MHz, Rate 54 Mb/s, Strength 58 WPA WPA2
    BTHomeHub2-3PTQ: Infra, 00:8B:5D:8F:9C:82, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    yasminesnetwork: Infra, 00:1F:33:FF:22:grin:C, Freq 2422 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             194.168.8.100


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             unavailable
  Default:           no
  HW Address:        C8:3A:35:C6:21:7F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


dell@dell-Latitude-D510:~$
Please be aware that I have tried to change/add info to the gedit?  following others instructions as I contacted Tenda, who weren't really  much help other than to point me to a driver download which I did follow  but failed to resolve anything.  The link is below for info:
 
   [http://www.ralinktech.com/support.php?s=2dr](http://www.ralinktech.com/support.php?s=2dr)
 
 I have also supplied an attachment supplied by Tendra, a picture of the  link indicating which driver/firmware to download.  Thought this might  be useful?
 
 Sorry for the long reply.
 
 Paul

---

### Post by Paul28799 on 2011-08-07
Is it possible that I need to reinstall a fresh copy of ubuntu to get rid of any errors I may have made in this OS? trying g to get it to work with the device?

---

### Post by lkjoel on 2011-08-07
You are connected to wireless with eth1.
Is your Trendnet device wlan0?

---

### Post by Paul28799 on 2011-08-07
The laptop wireless g device is on eth1 and when connected cable to router is eth0 but so far I have been unable to see my wireless N device other than when I ran those commands you kindly suggested previously.

---

### Post by lkjoel on 2011-08-07
> - Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             unavailable
  Default:           no
  HW Address:        C8:3A:35:C6:21:7F

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
This looks like a new wireless device.

Could you give me the output of this Terminal command?
```
sudo lspci -vvnn

```

---

### Post by Paul28799 on 2011-08-07
dell@dell-Latitude-D510:~$ sudo lspci -vvnn
[sudo] password for dell: 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
    Subsystem: Dell Device [1028:01af]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:01af]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
    Region 1: I/O ports at ec38 [size=8]
    Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Region 3: Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [d0] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
    Subsystem: Dell Device [1028:01af]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-

00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:01af]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at bf80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:01af]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 17
    Region 4: I/O ports at bf60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:01af]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at bf40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:01af]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 19
    Region 4: I/O ports at bf20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:01af]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME+
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
    Memory behind bridge: dfd00000-dfdfffff
    Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [50] Subsystem: Dell Device [1028:01af]

00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
    Subsystem: Dell Device [1028:01af]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at ed00 [size=256]
    Region 1: I/O ports at ec40 [size=64]
    Region 2: Memory at dfebfe00 (32-bit, non-prefetchable) [size=512]
    Region 3: Memory at dfebfd00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03) (prog-if 00 [Generic])
    Subsystem: Conexant Systems, Inc. Device [14f1:5423]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 17
    Region 0: I/O ports at ee00 [size=256]
    Region 1: I/O ports at ec80 [size=128]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel modules: snd-intel8x0m

00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
    Subsystem: Dell Device [1028:01af]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03) (prog-if 80 [Master])
    Subsystem: Dell Device [1028:01af]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 17
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at bfa0 [size=16]
    Capabilities: [70] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ata_piix
    Kernel modules: ahci

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at dfdfa000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME-
    Kernel driver in use: b44
    Kernel modules: b44

02:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
    Subsystem: Dell Device [1028:01af]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 168, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at dfd00000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
    Memory window 0: 80000000-83fff000 (prefetchable)
    Memory window 1: 84000000-87fff000
    I/O window 0: 00001400-000014ff
    I/O window 1: 00001800-000018ff
    BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

02:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments Device [104c:8037] (prog-if 10 [OHCI])
    Subsystem: Dell Device [1028:01af]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min, 1000ns max), Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 18
    Region 0: Memory at dfdf8800 (32-bit, non-prefetchable) [size=2K]
    Region 1: Memory at dfdfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [44] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME+
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection [8086:4223] (rev 05)
    Subsystem: Intel Corporation Device [8086:1021]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (750ns min, 6000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at dfdf9000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [dc] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=1 PME-
    Kernel driver in use: ipw2200
    Kernel modules: ipw2200

03:00.0 SATA controller [0106]: Initio Corporation INI-1623 PCI SATA-II Controller [1101:1622] (rev 02) (prog-if 00 [Vendor specific])
    Subsystem: Initio Corporation Device [1101:1626]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: I/O ports at 1400 [size=256]
    Region 1: Memory at 84000000 (32-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at 80000000 [disabled] [size=128K]
    Capabilities: [dc] Power Management version 2
        Flags: PMEClk+ DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: sata_inic162x
    Kernel modules: sata_inic162x

---

### Post by Paul28799 on 2011-08-07
its an old Dell Latitude D510 laptop but it works ok...except for this usb stick.

---

### Post by westie457 on 2011-08-07
Hi.

What is the output of ```
rfkill list all
```
with the device plugged in please

---

### Post by Paul28799 on 2011-08-07
dell@dell-Latitude-D510:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
dell@dell-Latitude-D510:~$

---

### Post by Paul28799 on 2011-08-07
The device is plugged in.  Thanks for you help and patience thus far.

---

### Post by lkjoel on 2011-08-07
lspci does not show your new wireless device, but both nm-tool and rfkill do.
Weird...

---

### Post by Paul28799 on 2011-08-07
never said it was going to be easy.....I've been banging my head with this one for a few days.  I have bought an Asus N13 to see if the issue is limited to the actual device?  Will post once it arrives......

---

### Post by westie457 on 2011-08-07
This might work.
Left-click on Network Manager icon, (top right of screen) select Edit Connections ..

In the Wireless tab select the one that matches the on-board wireless - hopefully you have only one here with Auto in the name - and then click Edit. Uncheck the Connect automatically box and then click Apply. Close Network Manager window. Left click the N M icon and disconnect from the wireless network for the on-board device.

Repeat the process for editing but this time for the USB device putting a check in the Connect automatically.

It is possible to have two wireless devices connected and running at the same time. However it is at the cost of greatly reduced connection speeds and is not recommended.

---

### Post by westie457 on 2011-08-07
> **lkjoel said:**
> lspci does not show your new wireless device, but both nm-tool and rfkill do.
Weird...

I had word blindness as well. It is a USB device. 

For the OP could you post result of ```
lsusb
``` with the thing plugged in please.

---

### Post by Paul28799 on 2011-08-07
dell@dell-Latitude-D510:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dell@dell-Latitude-D510:~$ 

sorry just got back in...info above as requested

---

### Post by Paul28799 on 2011-08-07
just to let you know I did follow your instruction posted two post ago, yes it is a USB device.  Still on the device when connected properly in Wins7 I(sorry - guess thats a dirty word here!) it has an LED that illuminates it is not so currently.

---

### Post by lkjoel on 2011-08-07
So it recognizes your wireless device. Apparently the wireless driver is installed too...

Download the attachment into your home directory.
Type in a Terminal window:
```
cd ~
chmod +x wireless.sh
./wireless.sh wlan0 ASUS

```

---

### Post by Paul28799 on 2011-08-07
no good, see below:

dell@dell-Latitude-D510:~$ cd ~
dell@dell-Latitude-D510:~$ chmod +x wireless.sh
chmod: cannot access `wireless.sh': No such file or directory
dell@dell-Latitude-D510:~$ ./wireless.sh wlan0 ASUS
bash: ./wireless.sh: No such file or directory
dell@dell-Latitude-D510:~$

Gotta go now will check post in morning thanks for all your time and help.

Paul

---

### Post by westie457 on 2011-08-07
It looks like you are using the wrong driver. Follow the information in this link [http://forums.whirlpool.net.au/archive/1650476](http://forums.whirlpool.net.au/archive/1650476) It has instructions and links to obtain and install the correct one.

---

### Post by Paul28799 on 2011-08-07
Thanks, I will try it in the morning and let you know how I get on.

---

### Post by Paul28799 on 2011-08-08
Thanks for the steer, I have read the info and have now got the correct driver.  Downloaded and extracted, see attached.

But what do I do with it, how do I get it to install and work with the device, this is all very new to me, could you show me what to do please?

It looks like I have to run it in terminal and modify some text code? But how to do so is still a mystery.

Thanks

Paul

---

### Post by westie457 on 2011-08-08
> **Paul28799 said:**
> Thanks for the steer, I have read the info and have now got the correct driver.  Downloaded and extracted, see attached.

But what do I do with it, how do I get it to install and work with the device, this is all very new to me, could you show me what to do please?

It looks like I have to run it in terminal and modify some text code? But how to do so is still a mystery.

Thanks

Paul

It is a mystery to me as well. I have only had to handle one .tar file in the last 3years and that was over a year ago so memory on what to do is very rusty. Any way here is a link for you. Some of the steps are necessary, some are not. If in doubt go through all of them in the order they are given substituting the correct file name for the ones given in the guide. [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

It should work very well.

Good luck.

---

### Post by lkjoel on 2011-08-08
The driver is a bit more complicated to install than: "make && sudo make install"

I'll post how to do it

---

### Post by Paul28799 on 2011-08-08
Thanks so much for your offer on how to do it and a post with instructions, that would be a great help.

---

### Post by Paul28799 on 2011-08-08
Thanks to Westie457 for all your help, will keep trying.

---

### Post by lkjoel on 2011-08-08
I guess I lied in my last post! It's actually really simple to install it.

Extract the driver, open a Terminal window, go to the directory of where you extracted the driver, and type in it:
```
sudo make
sudo make install

```
Reboot, and your driver is installed!

---

### Post by Paul28799 on 2011-08-08
if only it was so easeeeee!  Didn't work for me.....again.  Going to wait now until I get a new wireless stick delivered, guessing there might be an issue with this particular stick?

---

### Post by lkjoel on 2011-08-08
Could you give me the output of the commands above?

---

### Post by Paul28799 on 2011-08-08
I will but not tonight, had a rough day will have another look tomorrow, tried lots of different things begining to think I messed something up and considering reinstall ubuntu.  Will check back Tues.  Thanks again.

---

### Post by Paul28799 on 2011-08-09
Here we are:

 dell@dell-Latitude-D510:~$ cd ~
dell@dell-Latitude-D510:~$ sudo make
[sudo] password for dell: 
make: *** No targets specified and no makefile found. Stop.
dell@dell-Latitude-D510:~$ sudo make install
make: *** No rule to make target `install'. Stop.
dell@dell-Latitude-D510:~$ cd /home/downloads
bash: cd: /home/downloads: No such file or directory
dell@dell-Latitude-D510:~$ sudo make
make: *** No targets specified and no makefile found. Stop.
dell@dell-Latitude-D510:~$ sudo make install
make: *** No rule to make target `install'. Stop.
dell@dell-Latitude-D510:~$ 

Reasonably sure I am doing something wrong, the files for the driver are stored in  the home downloads directory.  Hope this helps.

Paul

---

### Post by lkjoel on 2011-08-09
[COLOR=Black]Try this:
[/COLOR]```
[COLOR=Black]mkdir DPO; cd DPO
wget http://dl.dropbox.com/u/21016209/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2
tar -xf [/COLOR][COLOR=Black]2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2
rm -f [/COLOR][COLOR=Black]2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2
cd [/COLOR][COLOR=Black]2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO
sudo make
sudo make install
[/COLOR]
```[COLOR=Black]
Then reboot, and see if you can connect.
[/COLOR]

---

### Post by Paul28799 on 2011-08-09
Hi lkjoel,  I did try your lats suggestion and a lot did happen but the laptop kept crashing I think during the final process, tried to reinstall ubuntu but kept having problems so I think they may have been a problem with the win7/linu dual boot or fauilty hard disk.  As it got late I intend to test the kit and try again later in the morning.
 
No I am not still trying at this time but the ...,.........dog just woke me up!  
 
Wanted to let you know of my progress with the problwm of wireless device today.
 
Thanks
 
Paul

---

### Post by Paul28799 on 2011-08-10
Ran the code this morning and the results are below just about to reboot to see if it works, just to make things more of a pain the hdd failed and have now replaced it:
dell@dell-Latitude-D510:~$ mkdir DPO; cd DPO
mkdir: cannot create directory `DPO': File exists
dell@dell-Latitude-D510:~/DPO$ wget [http://dl.dropbox.com/u/21016209/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2](http://dl.dropbox.com/u/21016209/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2)
--2011-08-10 11:16:36--  [http://dl.dropbox.com/u/21016209/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2](http://dl.dropbox.com/u/21016209/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2)
Resolving dl.dropbox.com... 50.17.206.117
Connecting to dl.dropbox.com|50.17.206.117|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 741780 (724K) [application/octet-stream]
Saving to: `2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2'

100%[======================================>] 741,780      394K/s   in 1.8s    

2011-08-10 11:16:38 (394 KB/s) - `2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2' saved [741780/741780]

dell@dell-Latitude-D510:~/DPO$ tar -xf 2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2
dell@dell-Latitude-D510:~/DPO$ rm -f 2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2
dell@dell-Latitude-D510:~/DPO$ cd 2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO
dell@dell-Latitude-D510:~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo make
[sudo] password for dell: 
Sorry, try again.
[sudo] password for dell: 
make -C tools
make[1]: Entering directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools'
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-10-generic/build SUBDIRS=/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/crypt_md5.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/crypt_aes.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/mlme.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_wep.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/action.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_data.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_init.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_init.c: In function &#8216;NICInitializeAsic&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_init.c:2173:17: warning: unused variable &#8216;irqFlag&#8217;
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_aes.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_sync.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/eeprom.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_info.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/dfs.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/spectrum.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_channel.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_profile.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicGetAutoAgcOffset&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c:878:10: warning: unused variable &#8216;bTempSuccess&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c:877:6: warning: unused variable &#8216;LookupTableIndex&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c:876:6: warning: unused variable &#8216;CurrentTemp&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c:875:8: warning: unused variable &#8216;BbpValue&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c:874:32: warning: unused variable &#8216;pTxPowerTuningEntry2&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c:871:8: warning: unused variable &#8216;RFValue&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c:870:32: warning: unused variable &#8216;pTxPowerTuningEntry&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicAdjustTxPower&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c:1524:20: warning: unused variable &#8216;pFinalTxPwr&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c:1522:11: warning: unused variable &#8216;bAutoTxAgc&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicEnableIbssSync&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c:2385:16: warning: unused variable &#8216;irqFlag&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c: In function &#8216;AsicAddPairwiseKeyEntry&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_asic.c:3124:16: warning: unused variable &#8216;irqFlag&#8217;
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/assoc.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/auth.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/sync.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/sanity.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/connect.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/connect.c: In function &#8216;LinkUp&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/connect.c:1481:35: warning: unused variable &#8216;pCurrEntry&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/connect.c:1480:28: warning: unused variable &#8216;HashIdx&#8217;
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/wpa.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/ags.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/sta_cfg.o
In file included from /usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/uaccess.h:571:0,
                 from /usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:211,
                 from /usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/include/os/rt_linux.h:40,
                 from /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/include/rtmp_os.h:44,
                 from /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/include/rtmp_comm.h:60,
                 from /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/include/rt_config.h:33,
                 from /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/sta_cfg.c:28:
In function &#8216;copy_from_user&#8217;,
    inlined from &#8216;RTMPSetInformation&#8217; at /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/sta_cfg.c:1712:28:
/usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/uaccess_32.h:212:26: warning: call to &#8216;copy_from_user_overflow&#8217; declared with attribute warning: copy_from_user() buffer size is not provably correct
In function &#8216;copy_from_user&#8217;,
    inlined from &#8216;RTMPSetInformation&#8217; at /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../sta/sta_cfg.c:2201:28:
/usr/src/linux-headers-2.6.38-10-generic/arch/x86/include/asm/uaccess_32.h:212:26: warning: call to &#8216;copy_from_user_overflow&#8217; declared with attribute warning: copy_from_user() buffer size is not provably correct
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_os_util.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../os/linux/rt_linux.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/ba_action.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_led.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:235:9: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:242:9: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:280:11: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c: In function &#8216;NICInitTransmit&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:509:12: warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:568:13: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:598:12: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:612:12: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:630:13: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RT28xx_UpdateBeaconToAsic&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_mac_usb.c:1392:16: warning: unused variable &#8216;irqFlag&#8217;
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtusb_io.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtusb_data.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/ee_prom.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/ee_efuse.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.c:415:13: warning: unused variable &#8216;pObj&#8217;
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_rf.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/frq_cal.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/frq_cal.c: In function &#8216;FrequencyCalibration&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/frq_cal.c:202:18: warning: comparison of distinct pointer types lacks a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/frq_cal.c:215:18: warning: comparison of distinct pointer types lacks a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/frq_cal.c:230:18: warning: comparison of distinct pointer types lacks a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/frq_cal.c:252:18: warning: comparison of distinct pointer types lacks a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/frq_cal.c:265:18: warning: comparison of distinct pointer types lacks a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/frq_cal.c:280:18: warning: comparison of distinct pointer types lacks a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/frq_cal.c:136:10: warning: unused variable &#8216;bUpdateRFR&#8217;
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt3070.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt30xx.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt30xx.c: In function &#8216;RT30xx_ChipSwitchChannel&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt30xx.c:612:17: warning: unused variable &#8216;BbpR109&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt30xx.c:611:30: warning: unused variable &#8216;Tx1FinePowerCtrl&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt30xx.c:611:8: warning: unused variable &#8216;Tx0FinePowerCtrl&#8217;
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt33xx.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt33xx.c: In function &#8216;RT33xxSetRxAnt&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt33xx.c:161:9: warning: unused variable &#8216;x&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt33xx.c: In function &#8216;RT33xx_ChipSwitchChannel&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt33xx.c:406:17: warning: unused variable &#8216;BbpR109&#8217;
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt3370.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt3370.c: In function &#8216;NICInitRT3370RFRegisters&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt3370.c:51:7: warning: unused variable &#8216;bbpreg&#8217;
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_Init&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:490:25: warning: assignment makes integer from pointer without a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390SetRxAnt&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:737:9: warning: unused variable &#8216;Value&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390LoadRFSleepModeSetup&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:839:8: warning: unused variable &#8216;RFValue&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390ReverseRFSleepModeSetup&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:915:8: warning: unused variable &#8216;RFValue&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_ChipSwitchChannel&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:1548:17: warning: comparison of distinct pointer types lacks a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:1559:17: warning: comparison of distinct pointer types lacks a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:1573:16: warning: comparison of distinct pointer types lacks a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:1443:17: warning: unused variable &#8216;BbpR110&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:1442:23: warning: unused variable &#8216;BbpR109&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c: In function &#8216;GetDesiredTssiAndCurrentTssi&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:3024:2: warning: missing braces around initializer
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:3024:2: warning: (near initialization for &#8216;htTssiInfo.PartA.field&#8217;)
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_ATETssiCalibration&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:3303:2: warning: ISO C90 forbids mixed declarations and code
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:3392:4: warning: passing argument 3 of &#8216;eFuseWrite&#8217; from incompatible pointer type
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/include/rtmp.h:5769:10: note: expected &#8216;PUSHORT&#8217; but argument is of type &#8216;UCHAR *&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:3304:42: warning: unused variable &#8216;ChannelPower&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c: In function &#8216;GetPowerDeltaFromTssiRatio&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:3534:2: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 4 has type &#8216;LONG&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:3563:2: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 3 has type &#8216;LONG&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c: In function &#8216;RT5390_AsicResetBbpAgent&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:3841:8: warning: unused variable &#8216;BBPValue&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../chips/rt5390.c:3840:8: warning: unused variable &#8216;loop&#8217;
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../os/linux/usb_main_dev.o
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c: In function &#8216;DefaultATEAsicSwitchChannel&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:1258:16: warning: comparison of distinct pointer types lacks a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:1044:21: warning: unused variable &#8216;RFValue2&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c: In function &#8216;ATETxPwrHandler&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:5338:45: warning: unused variable &#8216;CfgOfTxPwrCtrlOverMAC&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TX_FREQOFFSET_Proc&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:7750:13: warning: comparison of distinct pointer types lacks a cast
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TSSI_CALIBRATION_EX_Proc&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9476:9: warning: unused variable &#8216;CurrentChannel&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9475:9: warning: unused variable &#8216;BSSID_ADDR&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9474:10: warning: unused variable &#8216;ChannelPower&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9473:10: warning: unused variable &#8216;EEPData&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9472:31: warning: unused variable &#8216;TssiDeltaPerChannel&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9472:8: warning: unused variable &#8216;TssiRefPerChannel&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9471:53: warning: unused variable &#8216;BBP49Value&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9471:42: warning: unused variable &#8216;RF28Value&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9471:31: warning: unused variable &#8216;RF27Value&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9471:22: warning: unused variable &#8216;RFValue&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9471:9: warning: unused variable &#8216;BbpData&#8217;
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9479:1: warning: control reaches end of non-void function
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_TSSI_CALIBRATION_Proc&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:9463:1: warning: control reaches end of non-void function
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c: In function &#8216;DO_RACFG_CMD_ATE_E2PROM_READ_BULK&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:4017:1: warning: the frame size of 1028 bytes is larger than 1024 bytes
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c: In function &#8216;DO_RACFG_CMD_E2PROM_WRITE_ALL&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:3041:1: warning: the frame size of 1032 bytes is larger than 1024 bytes
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c: In function &#8216;DO_RACFG_CMD_ATE_E2PROM_WRITE_BULK&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:4050:1: warning: the frame size of 1040 bytes is larger than 1024 bytes
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c: In function &#8216;Set_ATE_Load_E2P_Proc&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rt_ate.c:8543:1: warning: the frame size of 1044 bytes is larger than 1024 bytes
  LD [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.o
see include/linux/module.h for more information
  CC      /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.mod.o
  LD [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
cp -f /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.ko /tftpboot
dell@dell-Latitude-D510:~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$

---

### Post by Paul28799 on 2011-08-10
And that did nothing, able to use the cable ethernet and wireless G but the N stick still not showing or any led on the device?

---

### Post by lkjoel on 2011-08-10
You forgot the last command.
Type these commands into a Terminal window:
```
cd ~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2  .5.0.2_DPO
sudo make install

```
Then reboot

---

### Post by Paul28799 on 2011-08-10
oK I have tried inputting the code in several ways as I was a little unsure, copied in all at once, rebooted, placed in sections by line and rebooted.  On each and every occasion nothing happened.  

Just to be sure its not my fault entering the code could you give me blow by blow code that needs to entered etc just to rule out any misunderstanding by me of your instructions that may be causing this issue.  I am copying and pasting the code so no errors there but concerned about which blocks to enter and when to strike enter.

Or there a different explanation?  Does it have to be so difficult!

---

### Post by lkjoel on 2011-08-10
Could you give me the output of the commands?

If it is really difficult, we could use TeamViewer.

---

### Post by Paul28799 on 2011-08-10
ok will run it again, can I put the code in as a oner in terminal, copy and paste if so could you please give me the whole code, just popping out back in 30 mins

---

### Post by Paul28799 on 2011-08-10
Ran it again, results as follows:

dell@dell-Latitude-D510:~$ mkdir DPO; cd DPO
mkdir: cannot create directory `DPO': File exists
dell@dell-Latitude-D510:~/DPO$ wget [http://dl.dropbox.com/u/21016209/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2](http://dl.dropbox.com/u/21016209/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2)
--2011-08-10 17:18:22--  [http://dl.dropbox.com/u/21016209/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2](http://dl.dropbox.com/u/21016209/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2)
Resolving dl.dropbox.com... 50.17.196.36
Connecting to dl.dropbox.com|50.17.196.36|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 741780 (724K) [application/octet-stream]
Saving to: `2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2'

100%[======================================>] 741,780      303K/s   in 2.4s    

2011-08-10 17:18:25 (303 KB/s) - `2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2' saved [741780/741780]

dell@dell-Latitude-D510:~/DPO$ tar -xf 2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2
dell@dell-Latitude-D510:~/DPO$ rm -f 2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2
dell@dell-Latitude-D510:~/DPO$ cd 2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO
dell@dell-Latitude-D510:~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo make
[sudo] password for dell: 
Sorry, try again.
[sudo] password for dell: 
make -C tools
make[1]: Entering directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools'
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-10-generic/build SUBDIRS=/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.c:415:13: warning: unused variable &#8216;pObj&#8217;
  LD [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.o
see include/linux/module.h for more information
  LD [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
cp -f /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.ko /tftpboot
dell@dell-Latitude-D510:~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo make
make -C tools
make[1]: Entering directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools'
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/Makefile
make -C /lib/modules/2.6.38-10-generic/build SUBDIRS=/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.o
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.c: In function &#8216;RtmpAsicSendCommandToMcu&#8217;:
/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/../../common/rtmp_mcu.c:415:13: warning: unused variable &#8216;pObj&#8217;
  LD [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.o
see include/linux/module.h for more information
  LD [M]  /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
cp -f /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/rt5370sta.ko /tftpboot
dell@dell-Latitude-D510:~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo make install
make -C /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-10-generic
make[1]: Leaving directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux'
dell@dell-Latitude-D510:~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ cd ~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2  .5.0.2_DPO
bash: cd: /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2: No such file or directory
dell@dell-Latitude-D510:~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo make install
make -C /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-10-generic
make[1]: Leaving directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux'
dell@dell-Latitude-D510:~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ cd ~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2  .5.0.2_DPO
bash: cd: /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2: No such file or directory
dell@dell-Latitude-D510:~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ sudo make install
make -C /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.38-10-generic
make[1]: Leaving directory `/home/dell/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux'
dell@dell-Latitude-D510:~/DPO/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO$ 


Is there a remote access available in ubuntu like in windows?  If so I am willing to try this if u can tell me how we go about setting this up to work?  What do you think?

---

### Post by lkjoel on 2011-08-10
Did you reboot?

For remote access, [http://www.teamviewer.com](http://www.teamviewer.com)
PM me your Teamviewer-ID and your Password, and I can help you.

---

### Post by Paul28799 on 2011-08-10
yes I did ok me a few minutes and I will look at remote

---

### Post by Paul28799 on 2011-08-10
error

---

### Post by Paul28799 on 2011-08-10
error

---

### Post by Paul28799 on 2011-08-10
the first settings is what was on the teamviewer window, the second lot was created by as a login a teamviewer web site?

not sure which one you needed so gave both.

---

### Post by Paul28799 on 2011-08-10
error post

---

### Post by lkjoel on 2011-08-10
I only need the first settings.

I'm online right now.

---

### Post by lkjoel on 2011-08-11
Try this in a Terminal window:
```
echo "blacklist rt2400pci
blacklist rt2500pci
blacklist rt2500usb
blacklist rt2800lib
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2860sta
blacklist rt2870sta
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Then reboot, recompile the driver, reboot, and see if it works.

---

### Post by Paul28799 on 2011-08-12
Hi Joel I have done as asked using the code listed below that you kindly supplied but I am a little unclear what is meant by complie the drive?  Could you explain please.
 
Paul
 
 
> **lkjoel said:**
> Try this in a Terminal window:
```
echo "blacklist rt2400pci
blacklist rt2500pci
blacklist rt2500usb
blacklist rt2800lib
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2860sta
blacklist rt2870sta
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Then reboot, recompile the driver, reboot, and see if it works.

---

### Post by lkjoel on 2011-08-12
I'll show you on Monday.

---

### Post by Paul28799 on 2011-08-15
Joel solved the problem and the solution is a s follows:

Open up a Terminal window, and type  in it: echo 'ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05",  ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"' | sudo  tee -a /etc/udev/rules.d/network_drivers.rules echo 'install rt2870sta  /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05  1784" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee -a  /etc/modprobe.d/network_drivers.c...

Many thanks for all Joel's time and support in finding this solution.

---

