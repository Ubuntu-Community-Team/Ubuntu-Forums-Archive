---
title: "Atheros 242x Hardware Switch OFF"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by eagles8804 on 2012-11-07
Hello everyone, I am currently running the latest version of Lubuntu, Lubuntu 12.01 on an old laptop. The laptop was given to me with Fedora BM on it but it kept crashing and then I finally installed Lubuntu on it and I am very pleased. NO CRASHES. Not to mention how nice Lubuntu is. However, I am experiencing this problem:

wlan wireless hardware is switched to OFF and when I run "rfkill" I learn that I am hard blocked.


#additional information: The laptop is an HP Pavilion Compaq Presario CQ50-115NR.

These are the commands I used to get to the point of which I am at:
<code>
lspci -vv
 (others omitted)...
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at c2000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [90] MSI-X: Enable- Count=1 Masked-
        Vector table: BAR=0 offset=00000000
        PBA: BAR=0 offset=00000000
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        AERCap:    First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
    Capabilities: [140 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
            Status:    NegoPending- InProgress-
    Kernel driver in use: ath5k
    Kernel modules: ath5k

sudo modprobe hp-wmi
rfkill unblock all
rfkill list all

0: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
1:phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

</code>  

Please help with the best of your abilities. All help will be appreciated. Thanks in advance.

P.S. This laptop is to be used as a temporary machine to compile code and do various programming tasks as I am just a beginner and a senior in high school. I am using this laptop until I can afford a better one for college. I do like the laptop but it is old, relatively unreliable, and there is not battery. For now it is my secondary desktop for reading in my room and when my mother is occupying the desktop in the den.

---

### Post by Danny Rafferty on 2013-01-09
I am also having the same problem. Using an Acer Aspire A150. This dis work previously.
Have tried madwifi to no avail.
12.04 reports that the interface is off and is not allowing me to activate it.

All help appreciated.

---

### Post by Danny Rafferty on 2013-01-09
Hey I think I have  a solution from here:
[http://ubuntuforums.org/showthread.php?t=1897031&highlight=ar242x+disabled+hard+blocked](http://ubuntuforums.org/showthread.php?t=1897031&highlight=ar242x+disabled+hard+blocked)

> **praseodym said:**
> Hi,

try this:

```
sudo modprobe -rfv ath5k
sudo rfkill unblock all
sudo modprobe -v ath5k
```
Check also the BIOS settings and/or reset the BIOS


Worked for me.....

---

