---
title: "Mac Mini sky2 gigabit performance issue"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by djwishbone on 2010-03-13
I'm trying to squeeze gigabit performance out of my mac mini without much luck.  It pretty much tops out at 14MB(yte)/sec.  Other machines on the same network and switch can do as much as 80MB/sec to each other.  I don't expect that out of this particular box, but I would expect to see something a little better than slightly above 100mb connection.

The connection is 1000Mb/s verified on both the mini and the switch.

Just upgraded to 9.10, but I've been running it on ubuntu since at least two releases and it has never had good gigabit performance.

Is this a hardware or module/driver problem?  I've seen lots of people complain about the sky2 driver.  Any help would be greatly appreciated.

uname -a
```
Linux chisa-2 2.6.31-20-generic-pae #57-Ubuntu SMP Mon Feb 8 10:23:59 UTC 2010 i686 GNU/Linux

```

lspci -vvv output:
```
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
        Subsystem: Marvell Technology Group Ltd. Device 5321
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 256 bytes
        Interrupt: pin A routed to IRQ 26
        Region 0: Memory at 90200000 (64-bit, non-prefetchable) [size=16K]
        Region 2: I/O ports at 1000 [size=256]
        Expansion ROM at 40000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data <?>
        Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
                Address: 00000000fee0300c  Data: 4181
        Capabilities: [e0] Express (v1) Legacy Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s unlimited, L1 unlimited
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 2048 bytes
                DevSta: CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 <256ns, L1 unlimited
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100] Advanced Error Reporting <?>
        Kernel driver in use: sky2
        Kernel modules: sky2

```

ethtool output:
```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes

```

Checking for bottlenecks with HDparm performance testing
```
/dev/sda:
 Timing cached reads:   2454 MB in  2.00 seconds = 1228.10 MB/sec
 Timing buffered disk reads:  110 MB in  3.04 seconds =  36.23 MB/sec

```

---

### Post by djwishbone on 2010-03-15
I compiled in the sk98lin driver and it was actually much worse in performance.  At this point I'm guessing the hardware is just not very good?

---

