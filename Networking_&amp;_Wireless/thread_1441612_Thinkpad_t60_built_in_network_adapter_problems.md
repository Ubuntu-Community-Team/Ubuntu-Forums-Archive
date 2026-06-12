---
title: "Thinkpad t60 built in network adapter problems"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by jackmakrl on 2010-03-29
Howdy,

I have a Thinkpad T60 running Ubuntu 9.10 2.6.31-20-generic #58-Ubuntu SMP 

Everything works great except the built in network controller doesn't work, it shows up with a lspci, but the e1000e module fails to initialize

02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
        Subsystem: Lenovo Device 2001
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at ee000000 (32-bit, non-prefetchable) [size=128K]
        Region 2: I/O ports at 3000 [size=32]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 00000000fee0300c  Data: 41b9
        Capabilities: [e0] Express (v1) Endpoint, MSI 00
                DevCap: MaxPayload 256 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
                DevCtl: Report errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <128ns, L1 <64us
                        ClockPM+ Suprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Device Serial Number 69-87-57-ff-ff-41-16-00
        Kernel modules: e1000e

here are the lines from /var/log/messages that relate to this:

Mar 28 19:34:27 nessie kernel: [    1.566429] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Mar 28 19:34:27 nessie kernel: [    1.566433] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Mar 28 19:34:27 nessie kernel: [    1.566491] e1000e 0000:02:00.0: Disabling L1 ASPM
Mar 28 19:34:27 nessie kernel: [    1.566512] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 28 19:34:27 nessie kernel: [    1.641387] e1000e 0000:02:00.0: PCI INT A disabled
Mar 28 19:34:27 nessie kernel: [    1.641399] e1000e: probe of 0000:02:00.0 failed with error -5

eth0 doesn't show up with a ifconfig -a

I remember trying to install 8.10 when it came out but gave up and haven't gotten around to installing linux on this system again, until now. A bunch of googling leads me to suspect that the nvram on the ethernet card may have been corrupted by the e1000e driver that came out with 8.10. When the Internal Network Option ROM setting is enabled in the BIOS (the default) the system doesn't boot cleanly and it spits out errors about how "the lan adaptors configuration is corrupted or has not been initalized" and "Expansion ROM not initialized" With the setting disabled it boots cleanly but won't work w/ linux. From what I gather XP ignores the ROM and has no problems.

I've seen references to fixes, but the one released by lenovo requires the card to show up as eth0 for the script to work. 

Is anyone familiar with this issue and/or have any suggestions for a solution?

Thanks,

Jack

---

### Post by chili555 on 2010-03-29
Here is a report that suggests that unloading and reloading the module works: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/328555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/328555)

Please try:> sudo rmmod -f e1000e
sudo modprobe e1000eThen check /var/log/messages for any improvement.

---

