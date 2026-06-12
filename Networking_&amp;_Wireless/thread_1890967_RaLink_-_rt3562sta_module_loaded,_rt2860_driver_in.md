---
title: "RaLink - rt3562sta module loaded, rt2860 driver in use!"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by zenon222 on 2011-12-04
I have referred to several methods of installing the RaLink driver from source code.

The rt3562sta driver is installed:
```
root@ubuntu-laptop:~# find /lib -name 'rt35*.ko'
/lib/modules/3.0.0-13-lowlatency/kernel/drivers/net/wireless/rt3562sta.ko
/lib/modules/3.0.0-13-lowlatency/kernel/drivers/staging/rt3562sta.ko
```But the kernel seems to still be "using" the WRONG driver rt2860:
```
root@ubuntu-laptop:~# lspci -vv
... lines removed ....

24:00.0 Network controller: RaLink Device 3592
    Subsystem: Hewlett-Packard Company Device 1638
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at d4600000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [70] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
            ClockPM+ Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Device Serial Number 68-a3-c4-a6-a7-4d-00-00
    Kernel driver in use: rt2860
    Kernel modules: rt3562sta
```However wlan0 is not up, and cannot come up
```
root@ubuntu-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 2c:41:38:01:21:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB)


root@ubuntu-laptop:~# ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
```

Any ideas on how to make the kernel to use the loaded rt3562sta module??????

---

