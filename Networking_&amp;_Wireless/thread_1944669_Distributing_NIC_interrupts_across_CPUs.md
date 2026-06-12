---
title: "Distributing NIC interrupts across CPUs"
date: 2012-03-21
forum: Networking &amp; Wireless
---

### Post by timjstewart on 2012-03-21
[FONT=Courier New][SIZE=1][B][SIZE=3]The Problem[/SIZE]
    
[/B][/SIZE][/FONT][FONT=Courier New][SIZE=1]The computer has 2 NICs: eth0 and eth2.  T[/SIZE][/FONT][FONT=Courier New][SIZE=1]he computer is running a Java application that services TCP  requests on both of the Ethernet adapters.  We would expect that we'd  see some interrupts on CPUs other than CPU 0 but all network related  interrupts happen only on [/SIZE][/FONT][FONT=Courier New][SIZE=1]CPU[/SIZE][/FONT][FONT=Courier New][SIZE=1] 0 (so says "cat /proc/interrupts")
  
How can we balance the interrupts across all (or at least more) CPUs?
  
Thanks in advance![/SIZE][/FONT]
[FONT=Courier New][SIZE=1][SIZE=3][B]
System Properties[/B][/SIZE]

[/SIZE][/FONT][FONT=Courier New][SIZE=1]Here are some commands I entered and their output:

**$ uname -a**
Linux arch 3.2.0-19-generic #31-Ubuntu SMP Wed Mar 21 02:11:53 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
[B]
$ dmesg | grep -i msi[/B]
[    1.338622] pcieport 0000:00:01.0: irq 72 for MSI/MSI-X
[    1.338733] pcieport 0000:00:03.0: irq 73 for MSI/MSI-X
[    1.338833] pcieport 0000:00:07.0: irq 74 for MSI/MSI-X
[   24.681248] bnx2 0000:03:00.0: irq 75 for MSI/MSI-X
[   24.681261] bnx2 0000:03:00.0: irq 76 for MSI/MSI-X
[   24.681270] bnx2 0000:03:00.0: irq 77 for MSI/MSI-X
[   24.681279] bnx2 0000:03:00.0: irq 78 for MSI/MSI-X
[   24.681288] bnx2 0000:03:00.0: irq 79 for MSI/MSI-X
[   24.681296] bnx2 0000:03:00.0: irq 80 for MSI/MSI-X
[   24.681305] bnx2 0000:03:00.0: irq 81 for MSI/MSI-X
[   24.681314] bnx2 0000:03:00.0: irq 82 for MSI/MSI-X
[   24.681322] bnx2 0000:03:00.0: irq 83 for MSI/MSI-X
[   24.743526] bnx2 0000:03:00.0: eth2: using MSIX
[   24.751352] bnx2 0000:01:00.0: irq 84 for MSI/MSI-X
[   24.751363] bnx2 0000:01:00.0: irq 85 for MSI/MSI-X
[   24.751372] bnx2 0000:01:00.0: irq 86 for MSI/MSI-X
[   24.751381] bnx2 0000:01:00.0: irq 87 for MSI/MSI-X
[   24.751391] bnx2 0000:01:00.0: irq 88 for MSI/MSI-X
[   24.751400] bnx2 0000:01:00.0: irq 89 for MSI/MSI-X
[   24.751408] bnx2 0000:01:00.0: irq 90 for MSI/MSI-X
[   24.751417] bnx2 0000:01:00.0: irq 91 for MSI/MSI-X
[   24.751426] bnx2 0000:01:00.0: irq 92 for MSI/MSI-X
[   24.815375] bnx2 0000:01:00.0: eth0: using MSIX


**$ lsb_release  -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu precise (development branch)
Release:    12.04
Codename:    precise

**$ sudo lspci -nn -vv -b**  # I omitted information that appeared to be irrelevant:
1:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5716 Gigabit Ethernet [14e4:163b] (rev 20)
        Subsystem: Dell PowerEdge R410 BCM5716 Gigabit Ethernet [1028:028c]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 15
        Region 0: Memory at d6000000 (64-bit, non-prefetchable)
        Capabilities: [48] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data
                Product Name: Broadcom NetXtreme II Ethernet Controller
                Read-only fields:
                        [PN] Part number: BCM95716C1
                        [EC] Engineering changes: 220197-3
                        [SN] Serial number: 0123456789
                        [MN] Manufacture ID: 31 30 32 38
                        [V0] Vendor specific: 5.0.12
                        [RV] Reserved: checksum good, 22 byte(s) reserved
                End
        [COLOR=Red]Capabilities: [58] MSI: Enable- Count=1/16 Maskable- 64bit+[/COLOR]
                Address: 0000000000000000  Data: 0000
       [/SIZE][/FONT][FONT=Courier New][SIZE=1][COLOR=Red] Capabilities: [a0] MSI-X: Enable+ Count=9 Masked-[/COLOR][/SIZE][/FONT][FONT=Courier New][SIZE=1]
                Vector table: BAR=0 offset=0000c000
                PBA: BAR=0 offset=0000e000
        Capabilities: [ac] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 512 bytes, PhantFunc 0, Latency L0s <4us, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal+ Fatal+ Unsupported+
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr+ NoSnoop+
                        MaxPayload 256 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x4, ASPM L0s L1, Latency L0 <2us, L1 <2us
                        ClockPM- Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+
                DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB
        Capabilities: [100 v1] Device Serial Number 00-26-b9-ff-fe-5d-27-82
        Capabilities: [110 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt+ UnxCmplt+ RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP+ FCP+ CmpltTO+ CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC+ UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP+ BadDLLP+ Rollover+ Timeout+ NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
        Capabilities: [150 v1] Power Budgeting <?>
        Capabilities: [160 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Kernel driver in use: bnx2
        Kernel modules: bnx2

01:00.1 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5716 Gigabit Ethernet [14e4:163b] (rev 20)
        Subsystem: Dell PowerEdge R410 BCM5716 Gigabit Ethernet [1028:028c]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 14
        Region 0: Memory at d8000000 (64-bit, non-prefetchable)
        Capabilities: [48] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data
                Product Name: Broadcom NetXtreme II Ethernet Controller
                Read-only fields:
                        [PN] Part number: BCM95716C1
                        [EC] Engineering changes: 220197-3
                        [SN] Serial number: 0123456789
                        [MN] Manufacture ID: 31 30 32 38
                        [V0] Vendor specific: 5.0.12
                        [RV] Reserved: checksum good, 22 byte(s) reserved
                End
        [COLOR=Red]Capabilities: [58] MSI: Enable- Count=1/16 Maskable- 64bit+[/COLOR]
                Address: 0000000000000000  Data: 0000
        [COLOR=Red]Capabilities: [a0] MSI-X: Enable- Count=9 Masked-[/COLOR]
                Vector table: BAR=0 offset=0000c000
                PBA: BAR=0 offset=0000e000
        Capabilities: [ac] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 512 bytes, PhantFunc 0, Latency L0s <4us, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal+ Fatal+ Unsupported+
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr+ NoSnoop+
                        MaxPayload 256 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x4, ASPM L0s L1, Latency L0 <2us, L1 <2us
                        ClockPM- Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+
                DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB
        Capabilities: [100 v1] Device Serial Number 00-26-b9-ff-fe-5d-27-83
        Capabilities: [110 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt+ UnxCmplt+ RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP+ FCP+ CmpltTO+ CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC+ UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP+ BadDLLP+ Rollover+ Timeout+ NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
        Capabilities: [150 v1] Power Budgeting <?>
        Capabilities: [160 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Kernel driver in use: bnx2
        Kernel modules: bnx2

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet [14e4:1639] (rev 20)
        Subsystem: Broadcom Corporation Device [14e4:0907]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 15
        Region 0: Memory at da000000 (64-bit, non-prefetchable)
        Capabilities: [48] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data
                Product Name: Broadcom NetXtreme II Ethernet Controller
                Read-only fields:
                        [PN] Part number: BCM95709A0907G
                        [EC] Engineering changes: 116322-10
                        [SN] Serial number: 0123456789
                        [MN] Manufacture ID: 31 30 32 38
                        [V0] Vendor specific: 5.0.12
                        [RV] Reserved: checksum good, 17 byte(s) reserved
                End
        [COLOR=Red]Capabilities: [58] MSI: Enable- Count=1/16 Maskable- 64bit+[/COLOR]
                Address: 0000000000000000  Data: 0000
        [COLOR=Red]Capabilities: [a0] MSI-X: Enable+ Count=9 Masked-[/COLOR]
                Vector table: BAR=0 offset=0000c000
                PBA: BAR=0 offset=0000e000
        Capabilities: [ac] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 512 bytes, PhantFunc 0, Latency L0s <4us, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal+ Fatal+ Unsupported+
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr+ NoSnoop+
                        MaxPayload 256 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x4, ASPM L0s L1, Latency L0 <2us, L1 <2us
                        ClockPM- Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+
                DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB
        Capabilities: [100 v1] Device Serial Number 00-10-18-ff-fe-5d-b1-18
        Capabilities: [110 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt+ UnxCmplt+ RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP+ FCP+ CmpltTO+ CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC+ UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP+ BadDLLP+ Rollover+ Timeout+ NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
        Capabilities: [150 v1] Power Budgeting <?>
        Capabilities: [160 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Kernel driver in use: bnx2
        Kernel modules: bnx2
03:00.1 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet [14e4:1639] (rev 20)
        Subsystem: Broadcom Corporation Device [14e4:0907]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 14
        Region 0: Memory at dc000000 (64-bit, non-prefetchable)
        Capabilities: [48] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data
                Product Name: Broadcom NetXtreme II Ethernet Controller
                Read-only fields:
                        [PN] Part number: BCM95709A0907G
                        [EC] Engineering changes: 116322-10
                        [SN] Serial number: 0123456789
                        [MN] Manufacture ID: 31 30 32 38
                        [V0] Vendor specific: 5.0.12
                        [RV] Reserved: checksum good, 17 byte(s) reserved
                End
        [COLOR=Red]Capabilities: [58] MSI: Enable- Count=1/16 Maskable- 64bit+[/COLOR]
                Address: 0000000000000000  Data: 0000
        [COLOR=Red]Capabilities: [a0] MSI-X: Enable- Count=9 Masked-[/COLOR]
                Vector table: BAR=0 offset=0000c000
                PBA: BAR=0 offset=0000e000
        Capabilities: [ac] Express (v2) Endpoint, MSI 00
                DevCap: MaxPayload 512 bytes, PhantFunc 0, Latency L0s <4us, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal+ Fatal+ Unsupported+
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr+ NoSnoop+
                        MaxPayload 256 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x4, ASPM L0s L1, Latency L0 <2us, L1 <2us
                        ClockPM- Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x4, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
                DevCap2: Completion Timeout: Range ABCD, TimeoutDis+
                DevCtl2: Completion Timeout: 65ms to 210ms, TimeoutDis-
                LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
                         Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
                         Compliance De-emphasis: -6dB
                LnkSta2: Current De-emphasis Level: -6dB
        Capabilities: [100 v1] Device Serial Number 00-10-18-ff-fe-5d-b1-1a
        Capabilities: [110 v1] Advanced Error Reporting
                UESta:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UEMsk:  DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt+ UnxCmplt+ RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
                UESvrt: DLP+ SDES+ TLP+ FCP+ CmpltTO+ CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC+ UnsupReq- ACSViol-
                CESta:  RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
                CEMsk:  RxErr- BadTLP+ BadDLLP+ Rollover+ Timeout+ NonFatalErr+
                AERCap: First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
        Capabilities: [150 v1] Power Budgeting <?>
        Capabilities: [160 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Kernel driver in use: bnx2
        Kernel modules: bnx2

[B]$ cat /proc/cpuinfo
[/B]processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 26
model name      : Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
stepping        : 5
microcode       : 0x11
cpu MHz         : 1596.085
cache size      : 8192 KB
physical id     : 1
siblings        : 4
core id         : 0
cpu cores       : 4
apicid          : 16
initial apicid  : 16
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopo
logy nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips        : 3192.17
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management:

:
:  cores 1 - 6 omitted
:

processor       : 7
vendor_id       : GenuineIntel
cpu family      : 6
model           : 26
model name      : Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz
stepping        : 5
microcode       : 0x11
cpu MHz         : 1596.085
cache size      : 8192 KB
physical id     : 0
siblings        : 4
core id         : 3
cpu cores       : 4
apicid          : 6
initial apicid  : 6
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca sse4_1 sse4_2 popcnt lahf_lm ida dts tpr_shadow vnmi flexpriority ept vpid
bogomips        : 3191.89
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management:[B]

$ cat /proc/interrupts 
[/B]            CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7       
   0:     411190          0          0          0          0          0          0          0   IO-APIC-edge      timer
   1:          3          0          0          0          0          0          0          0   IO-APIC-edge      i8042
   8:          1          0          0          0          0          0          0          0   IO-APIC-edge      rtc0
   9:          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   acpi
  12:          4          0          0          0          0          0          0          0   IO-APIC-edge      i8042
  17:          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
  18:          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb4
  19:         25          0          0          0          0          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb1
  20:          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   uhci_hcd:usb6, uhci_hcd:usb8
  21:         54          0          0          0          0          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb5, uhci_hcd:usb7
  22:         63          0          0          0          0          0          0          0   IO-APIC-fasteoi   ata_piix
  23:          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   ata_piix
  32:      12439          0          0          0          0          0          0          0   IO-APIC-fasteoi   ioc0
  72:          0          0          0          0          0          0          0          0   PCI-MSI-edge      PCIe PME
  73:          0          0          0          0          0          0          0          0   PCI-MSI-edge      PCIe PME
  74:          0          0          0          0          0          0          0          0   PCI-MSI-edge      PCIe PME
  75:        514          0          0          0          0          0          0          0   PCI-MSI-edge      eth2-0
  76:    1168030          0          0          0          0          0          0          0   PCI-MSI-edge      eth2-1
  77:    1170834          0          0          0          0          0          0          0   PCI-MSI-edge      eth2-2
  78:      17905          0          0          0          0          0          0          0   PCI-MSI-edge      eth2-3
  79:        512          0          0          0          0          0          0          0   PCI-MSI-edge      eth2-4
  80:     516127          0          0          0          0          0          0          0   PCI-MSI-edge      eth2-5
  81:          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth2-6
  82:      18102          0          0          0          0          0          0          0   PCI-MSI-edge      eth2-7
  84:     362612          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-0
  85:     811671          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-1
  86:     834528          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-2
  87:     809188          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-3
  88:     712879          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-4
  89:     734798          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-5
  90:     750644          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-6
  91:     815346          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-7
 NMI:        499        106        235        109        177        106        135        105   Non-maskable interrupts
 LOC:     159293      90543     123092     100445     105701     117253      90064     139456   Local timer interrupts
 SPU:          0          0          0          0          0          0          0          0   Spurious interrupts
 PMI:        499        106        235        109        177        106        135        105   Performance monitoring interrupts
 IWI:          0          0          0          0          0          0          0          0   IRQ work interrupts
 RES:     129296     929550     658596     926913     518932     947506     451426     946255   Rescheduling interrupts
 CAL:        223       5693        246        260        291        285        276        290   Function call interrupts
 TLB:       7639       3087       4668       3450       4311       2888       3674       3017   TLB shootdowns
 TRM:          0          0          0          0          0          0          0          0   Thermal event interrupts
 THR:          0          0          0          0          0          0          0          0   Threshold APIC interrupts
 MCE:          0          0          0          0          0          0          0          0   Machine check exceptions
 MCP:         24         24         24         24         24         24         24         24   Machine check polls
 ERR:          0
 MIS:          0
[B]
$ /opt/jdk1.6.0_16/bin/java -version
[/B]java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) 64-Bit Server VM (build 14.2-b01, mixed mode)
[/SIZE][/FONT][FONT=Courier New][SIZE=1]

[/SIZE][/FONT]

---

