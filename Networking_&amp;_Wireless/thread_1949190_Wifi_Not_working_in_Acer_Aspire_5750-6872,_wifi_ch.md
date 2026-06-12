---
title: "Wifi Not working in Acer Aspire 5750-6872, wifi chip is Intel Centrino Advanc N 6205"
date: 2012-03-29
forum: Networking &amp; Wireless
---

### Post by VirgoLinux on 2012-03-29
Wireless Card On my Acer Laptop  is not working in Ubuntu 10.04 LTS. 
Following are my systerm details 

**1 ) Machine Brand and Model (Laptop)**:
 ```
Acer Aspire 5750-6872
```[B]2 ) Wireless Brand, Model and Wireless Chipset
[/B]```
# lspci -nnvvk
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0082] (rev 34)
    Subsystem: Intel Corporation Device [8086:1301]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 7
    Region 0: Memory at c0500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [e0] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ FLReset-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <32us
            ClockPM+ Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Device Serial Number ac-90-b0-ff-ff-96-11-08
```**3 ) check interface:**
```
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
# 
```**4 ) Check for modules/drivers:**
```
# lsmod | grep -i iwlagn
# 

# lsmod | grep mac
# 
```**Network configuration**
```
# lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: dc:0e:a1:10:ae:8b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.122g duplex=full firmware=sb ip=192.168.11.22 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:c0430000-c043ffff(prefetchable) memory:c0440000-c044ffff(prefetchable) memory:c0450000-c04507ff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0500000-c0501fff
# 
```**Ubuntu/Kernel Version**
```
# uname -mr
2.6.32-40-generic-pae i686
# 
# lsb_release -d
Description:    Ubuntu 10.04.4 LTS
# 
# 
```I googled around for the solution and I think that the intel wireless driver iwlagn should work. There are Ko modules present in my system as follows but they are not loaded by default. Also I tried to load them using insmod but still my wireless was not working. It is also mentioned at [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) that this drivers are already present in kernel version > 2.6.24 Which is true for my ubuntu installation 
```
# modprobe -v iwlagn
insmod /lib/modules/2.6.32-40-generic-pae/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/2.6.32-40-generic-pae/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/2.6.32-40-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlcore.ko 
insmod /lib/modules/2.6.32-40-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

# 
```

---

### Post by chili555 on 2012-03-29
How about letting us see the result of these commands:```
sudo modprobe iwlagn
dmesg | grep iwl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

