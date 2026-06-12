---
title: "Jaunty 'Hides' WPA/WPA2 Option"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by keryil on 2009-07-14
Hi all,
I have a peculiar problem. When I try to connect to a wireless router (Arcadyan WG4005G based) which uses WPA/WPA2, using the "wireless list" in the tray, I get a "authentication required" dialogue, which only lists a bunch of WEPs and a LEAP as encryption options. I can, however, regularly connect to another router over WPA/WPA2. What's more interesting is that if I specify that I want WPA/WPA2 encryption in "Network Connections" (I guess this is gnome's network manager) my computer does connect. The question is, why is that not an option when I try to connect the first time?

You might have noticed that this is not a huge issue since there is a workaround. Still curious though, and I suspect a lot of newcomers might bump into similar stuff and give it up altogether.

I am using an HP DV4 laptop. And here is some extremely verbose info about the wireless hardware, just in case:

```
04:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation Device 1211
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 2294
	Region 0: Memory at dc200000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
		Address: 00000000fee0300c  Data: 41d1
	Capabilities: [e0] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ FLReset-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <128ns, L1 <32us
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number f4-12-d6-ff-ff-ea-16-00
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn
```

**Later Note:** It turns out I have lost the ability to reproduce the situation on my laptop. However, before this, I briefly saw two instances of the same network, one of them used WPA/2 as it should, and the other insisted on WEP and LEAP. No matter if I delete the configuration now, though, can I get the mentioned malfunction again. I suspect what made the change was that I enabled the manually configured connection for all users (which I had not before).

This gives signals of becoming a thought experiment than a bug-bust, but still. Any ideas?

---

