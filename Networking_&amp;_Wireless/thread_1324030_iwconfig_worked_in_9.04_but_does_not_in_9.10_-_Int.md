---
title: "iwconfig worked in 9.04 but does not in 9.10 - Intel PRO/Wireless 5100 AGN"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by anomenat on 2009-11-12
Hello,

I have a Lenovo Thinkpad X200, which has an Intel PRO/Wireless 5100 AGN wireless networking adaptor. Output from [FONT=Courier New]lspci -vv[FONT=Verdana] included below.[/FONT][/FONT]

I have been using Ubuntu 9.04 for a few months now. By default, power management is not enabled on the wireless device, which results in the fan running noisily at high speed all the time. However, by running [FONT=Courier New]iwconfig wlan0 power on[FONT=Verdana] as root I was able to turn power management on, which means the fan only spins at high speed when it should (i.e. when I am transmitting or receiving a lot of data over wireless for a long period of time) and is quiet the rest of the time.

Yesterday, I upgraded to Ubuntu 9.10 and [FONT=Courier New]iwconfig[FONT=Verdana] no longer works. I receive the following output:

[FONT=Courier New]Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
[FONT=Verdana]
Any idea why it no longer works? It is rather annoying, as the fan is now very noisy all the time, which isn't really acceptable.

Here is the relevant bit of output from [FONT=Courier New]lspci -vv[FONT=Verdana]:

[FONT=Courier New]03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
        Subsystem: Intel Corporation Device 1211
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 30
        Region 0: Memory at f2500000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
                Address: 00000000fee0300c  Data: 41b9
        Capabilities: [e0] Express (v1) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ FLReset-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <128ns, L1 <32us
                        ClockPM+ Suprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Device Serial Number cc-a6-33-ff-ff-fa-22-00
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

[FONT=Verdana]Can anyone help?

Thank you very much,

Charles
[/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT][/FONT]

---

### Post by bgenc on 2009-11-12
I have a similar problem. I cannot set tx-power value. I get the same warning/error.

---

### Post by anomenat on 2009-11-12
[FONT=Courier New]$ uname -mr
2.6.31-14-generic x86_64

[/FONT]

---

### Post by motoko28 on 2009-12-26
Same problem here, i was using it to reduce the power consumption when i was using the battery. That reduced the power consumption  1 or 2 Watts, and in the ubuntu 9.10 is no longer working. Anyone can help here?

---

