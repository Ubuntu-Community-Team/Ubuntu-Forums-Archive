---
title: "TV-Station DVB-S2 Twin"
date: 2012-09-03
forum: Multimedia Software
---

### Post by aasgaa on 2012-09-03
[FONT=Arial][FONT=Arial]I have the following Tvheadend installation:[/FONT]
[FONT=Arial]• Ubuntu server 12.04[/FONT]
[FONT=Arial]• Kernel version 3.2.0-29-generic x86_64[/FONT]
[FONT=Arial]• KNC1 TV-Station DVB-S2 Twin card[/FONT][/FONT]
[FONT=Arial][[FONT=Arial][COLOR=#800080]http://knc1.de/d/produkte/digital_dvb_s2_twin.htm[/COLOR][/FONT]]("http://knc1.de/d/produkte/digital_dvb_s2_twin.htm")[/FONT]
 
[FONT=Arial][FONT=Arial]KNC1 are providing a Linux driver on their homepage [/FONT][[FONT=Arial]http://knc1.de/d/download/digital.htm#linux[/FONT]]("http://knc1.de/d/download/digital.htm#linux")[FONT=Arial].[/FONT][/FONT]
 
[FONT=Arial][FONT=Arial]During the build of the driver, I get a lot of warnings – and one error.[/FONT][/FONT]
[FONT=Arial][FONT=Arial]Still, the build completes, and the driver loads.[/FONT][/FONT]
 
[FONT=Arial][FONT=Arial]Configuring the DVB-S2 card in TVheadend works fine, and I’m able to scan for Muxes and services. It’s even possible to bring TV to the screen via XBMC. [/FONT][/FONT]
 
[FONT=Arial][FONT=Arial]But here it ends. The system is not able to show the picture in proper quality. HDTV is useless – even standard TV resolution is not acceptable.[/FONT][/FONT]
 
[FONT=Arial][FONT=Arial]syslog is logging a lot of the following entries:[/FONT][/FONT]
[FONT=Arial]Sep 3 07:03:10 ubtv01 tvheadend[1076]: TS: STV090x Multistandard/11,836,500 kHz Horizontal (No satconf)/Das Erste: MPEG2VIDEO @ #101: Continuity counter error, 10 dup$[/FONT]
[FONT=Arial]Sep 3 07:03:10 ubtv01 tvheadend[1076]: TS: STV090x Multistandard/11,836,500 kHz Horizontal (No satconf)/Das Erste: TELETEXT @ #104: Continuity counter error[/FONT]
 
[FONT=Arial]**lspci –vv **gives the following output:[/FONT]
[FONT=Arial]04:00.0 Multimedia controller: Philips Semiconductors SAA7160 (rev 02)[/FONT]
[FONT=Arial]Subsystem: KNC One Device 0210[/FONT]
[FONT=Arial]Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-[/FONT]
[FONT=Arial]Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-[/FONT]
[FONT=Arial]Latency: 0, Cache Line Size: 32 bytes[/FONT]
[FONT=Arial]Interrupt: pin A routed to IRQ 16[/FONT]
[FONT=Arial]Region 0: Memory at f6a00000 (64-bit, non-prefetchable) [size=1M][/FONT]
[FONT=Arial]Capabilities: [40] MSI: Enable- Count=1/32 Maskable- 64bit+[/FONT]
[FONT=Arial]Address: 0000000000000000 Data: 0000[/FONT]
[FONT=Arial]Capabilities: [50] Express (v1) Endpoint, MSI 00[/FONT]
[FONT=Arial]DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <256ns, L1 <1us[/FONT]
[FONT=Arial]ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-[/FONT]
[FONT=Arial]DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-[/FONT]
[FONT=Arial]RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-[/FONT]
[FONT=Arial]MaxPayload 128 bytes, MaxReadReq 128 bytes[/FONT]
[FONT=Arial]DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-[/FONT]
[FONT=Arial]LnkCap: Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us[/FONT]
[FONT=Arial]ClockPM- Surprise- LLActRep- BwNot-[/FONT]
[FONT=Arial]LnkCtl: ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk-[/FONT]
[FONT=Arial]ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-[/FONT]
[FONT=Arial]LnkSta: Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-[/FONT]
[FONT=Arial]Capabilities: [74] Power Management version 2[/FONT]
[FONT=Arial]Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot-,D3cold-)[/FONT]
[FONT=Arial]Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-[/FONT]
[FONT=Arial]Capabilities: [80] Vendor Specific Information: Len=50 <?>[/FONT]
[FONT=Arial]Capabilities: [100 v1] Vendor Specific Information: ID=0000 Rev=0 Len=088 <?>[/FONT]
[FONT=Arial]Kernel driver in use: SAA716x Budget[/FONT]
[FONT=Arial]Kernel modules: **saa716x_budget**[/FONT]
 
[FONT=Arial][FONT=Arial]Anybody out there having experience with the **TV-Station DVB-S2 Twin **under Linux?[/FONT][/FONT]
 
[FONT=Arial][FONT=Arial]Any suggestions how to proceed from here?[/FONT][/FONT]
[FONT=Arial][FONT=Arial]Thanks![/FONT][/FONT]

---

### Post by aasgaa on 2012-10-17
Trying again...

---

