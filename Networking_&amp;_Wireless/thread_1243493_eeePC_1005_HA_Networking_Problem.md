---
title: "eeePC 1005 HA Networking Problem"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by Nubnut on 2009-08-18
I have just taken delivery of a new EeePc 1005 HA Netbook and installed 9.04 on it. Ethernet and wireless are not working. I've tried installing the new driver as per the instructions here [http://ubuntuforums.org/showthread.php?t=1219931]("http://ubuntuforums.org/showthread.php?t=1219931")
The driver AR813X-linux-v1.0.0.9.tar.gz waz not available on the Atheros website so I used AR81Family-linux-v1.0.0.10.tar.gz instead. This did not work.
I cannot find AR813X-linux-v1.0.0.9.tar.gz for download anywhere.

Below is the output of the relevant section of lspci -vvv

01:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device 838a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 2299
	Region 0: Memory at f7fc0000 (64-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at ec00 [size=128]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
		Address: 00000000fee0300c  Data: 4199
	Capabilities: [58] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 4096 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag- AttnBtn+ AttnInd+ PwrInd+ RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 unlimited, L1 unlimited
			ClockPM+ Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [6c] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [180] Device Serial Number ff-18-26-00-ca-83-5f-ff
	Kernel driver in use: atheros_eth
	Kernel modules: atl1e

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Device 1a3b:1089
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express (v2) Legacy Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <512ns, L1 <64us
			ClockPM- Suprise- LLActRep- BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM-
 AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 12-14-24-ff-ff-17-15-00
	Capabilities: [170] Power Budgeting <?>


Any help with this would be greatly appreciated.

---

### Post by fourthirtysix on 2009-08-18
try this

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

---

### Post by Nubnut on 2009-08-19
Unfortunately this hasn't worked for me.
I downloaded and installed UNR ok.
Then downloaded the Atheros wired driver, copied to usb, transferred onto netbook and installed.

'make' ran ok
but the last lines of the 'sudo make install' output read
'cannot write to /var/cache/man/cat7/atl1e.7.gz in catman mode
atl1e.'
I ran 'sudo insmod atl1e.ko' anyway and tested - network card not working.

So then I followed the instructions to ensure that I have the correct linux Headers installed, - and then re-installed the atheros driver as per instructions - still not working, so uninstalled atheros driver using 'sudo rmmod atl1e.ko' and re-installed - still not working.

I'm at a loss as to what to do next.

Thanks for your help so far with this fourthirtysix, your instructions are very clear and easy to follow, if you or anyone else have any further advice please reply.

I'm configuring this Netbook for use in a School, once this one is sorted 250 more will be cloned from it for use by our students - school's back the week after next and I'm starting to feel under pressure.

Any and all help appreciated!!

---

### Post by Nubnut on 2009-08-19
There is one further possibility, the card may be working without me knowing it!!
I just disabled wireless on the laptop I'm using to post this, just to force it to use the wired connection and the connection died. I'm in the school and dont have access to reboot the wired network so am heading home to test there,.........will report asap.

---

### Post by Nubnut on 2009-08-19
I just cheked on home network and all now working, thanks a million fourthirtysix!!
I'm now in the process of fixing the wireless,........ school rollout should happen as scheduled.

nnuts

---

### Post by L2linux on 2009-08-19
> **fourthirtysix said:**
> try this

[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)

That site workers wonders, but remember he's using the Netbook Remix.

---

### Post by nathanpc on 2009-08-19
I'm having a issue that is like this: [http://ubuntuforums.org/showthread.php?t=1244774]("http://ubuntuforums.org/showthread.php?t=1244774").
If someone can help me, thanks!

---

### Post by Nubnut on 2009-08-19
Ooops, replying here to a thread since deleted, advised by L2Linux that 436 is using UNR....


Yeah, and as soon as I got his reply I started using UNR (Ubuntu Netbook Remix) too. I didn't think there'd be much difference but boot-wise it's very significant.
I ran into more issues since - with the wireless config which should have been painless,......once i'd enabled jaunty backports i allowed synaptic to follow it's default course of action which is to install all backports - **dont do this** - it broke my ethernet - I ended up re-installing UNR (only took about 15 - 20 minutes) and reinstalling the driver as per instrucions. See[ http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/]("http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/")
After I enabled jaunty backports I ran synaptic and selected *******only****** 'linux-backports-modules-jaunty'

*an aside* - synaptic's search function is a little jaded - if you look for the exact string of what you're looking for it doesnt find - do a very generic search and use your eyes

Ainhows, wireless now working, yaaay, thanks 436 - if i dont crashout soon I'll be callin myself twoOhseven

done a bit, fixed a bit, learned a bit, out

Ro

Thanks again fourthirtysix, L2linux , and the U forums, 

ps - i made some straightforward stuff into an odyssey, maybe I'll change my name from nubnut to numbnuts

---

