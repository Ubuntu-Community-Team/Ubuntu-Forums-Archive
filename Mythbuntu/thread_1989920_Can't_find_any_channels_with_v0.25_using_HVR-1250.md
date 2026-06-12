---
title: "Can't find any channels with v0.25 using HVR-1250"
date: 2012-05-29
forum: Mythbuntu
---

### Post by nhtrader on 2012-05-29
I can't get Hauppauge HVR-1250 to work with new install of MythTV v0.25/Ubuntu 12.04 (64bit). But verified that it works on Windows. Also, this card worked fine on MythTV v0.23 and v0.24. Now doesn't work on v0.25.

Don't know what to do next. Any ideas...


 Here's what I did to diagnose problem and don't know what to do next...

1. Verified TV Capture Card works on a WinXP.

2. On Mythbuntu 12.04-v0.25 Fresh Install below are the commands used for diagnostic purposes:

```

sudo su
dmesg|grep cx23885  (output below)
	[   16.178221] cx23885 driver version 0.0.3 loaded
	[   16.178601] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
	[   16.178785] CORE cx23885[0]: subsystem: 0070:2211, board: Hauppauge WinTV-HVR1270 [card=18,autodetected]
	[   16.325679] cx23885[0]: hauppauge eeprom: model=22111
	[   16.368096] cx25840 2-0044: cx23888 A/V decoder found @ 0x88 (cx23885[0])
	[   17.086276] cx25840 2-0044: loaded v4l-cx23885-avcore-01.fw firmware (16382 bytes)
	[   17.094833] cx23885_dvb_register() allocating 1 frontend(s)
	[   17.094838] cx23885[0]: cx23885 based dvb card
	[   17.332720] DVB: registering new adapter (cx23885[0])
	[   17.333047] cx23885_dev_checkrevision() Hardware revision = 0xd0
	[   17.333052] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfd600000
	[   17.333060] cx23885 0000:02:00.0: setting latency timer to 64
	[   17.356147] input: cx23885 IR (Hauppauge WinTV-HVR1270) as /devices/pci0000:00/0000:00:04.0/0000:02:00.0/rc/rc0/input12
	[   17.356215] rc0: cx23885 IR (Hauppauge WinTV-HVR1270) as /devices/pci0000:00/0000:00:04.0/0000:02:00.0/rc/rc0
	[   17.356285] input: MCE IR Keyboard/Mouse (cx23885) as /devices/virtual/input/input13
	[   17.356358] rc rc0: lirc_dev: driver ir-lirc-codec (cx23885) registered at minor = 0

sudo su
lspci -vvnn   (output below)
  02:00.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb [14f1:8880] (rev 04)
	Subsystem: Hauppauge computer works Inc. Device [0070:2211]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fd600000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 512 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <2us, L1 <4us
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [80] Power Management version 3
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [90] Vital Product Data
		Unknown small resource type 01, will not decode more.
	Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
	Capabilities: [200 v1] Virtual Channel
		Caps:	LPEVC=1 RefClk=100ns PATEntryBits=1
		Arb:	Fixed+ WRR32+ WRR64+ WRR128-
		Ctrl:	ArbSelect=WRR64
		Status:	InProgress-
		Port Arbitration Table [240] <?>
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
		VC1:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable- ID=1 ArbSelect=Fixed TC/VC=00
			Status:	NegoPending- InProgress-
	Kernel driver in use: cx23885
	Kernel modules: cx23885

lshw -C multimedia   (output below)
       description: Multimedia video controller
       product: CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: driver=cx23885 latency=0
       resources: irq:16 memory:fd600000-fd7fffff


sudo su
lsof /dev/dvb/adapter0/frontend0   (output below)
	COMMAND    PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
	mythbacke 1822 mythtv   11u   CHR  212,0      0t0 8299 /dev/dvb/adapter0/frontend0
stop mythtv-backend
scan /usr/share/dvb/atsc/us-Cable-HRC-center-frequencies-QAM256   (output)
	scanning /usr/share/dvb/atsc/us-Cable-HRC-center-frequencies-QAM256
	using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
	>>> tune to: 73753600:QAM_256
	WARNING: >>> tuning failed!!!
	>>> tune to: 73753600:QAM_256 (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 55752700:QAM_256
	WARNING: >>> tuning failed!!!
	>>> tune to: 55752700:QAM_256 (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 61753000:QAM_256
	WARNING: >>> tuning failed!!!
	>>> tune to: 61753000:QAM_256 (tuning failed)
	WARNING: >>> tuning failed!!!


scan /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256   (output below)
	scanning /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256
	using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
	>>> tune to: 57000000:QAM_256
	WARNING: >>> tuning failed!!!
	>>> tune to: 57000000:QAM_256 (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 63000000:QAM_256
	WARNING: >>> tuning failed!!!
	>>> tune to: 63000000:QAM_256 (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 69000000:QAM_256
	WARNING: >>> tuning failed!!!


scan /usr/share/dvb/atsc/us-MA-Boston   (output below)
	scanning /usr/share/dvb/atsc/us-MA-Boston
	using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
	>>> tune to: 503000000:8VSB
	WARNING: >>> tuning failed!!!
	>>> tune to: 503000000:8VSB (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 509000000:8VSB
	WARNING: >>> tuning failed!!!
	>>> tune to: 509000000:8VSB (tuning failed)
	WARNING: >>> tuning failed!!!
	>>> tune to: 527000000:8VSB

installed w-scan (not w_scan)
sudo su
apt-get install w-scan

w_scan -ft -A2 -t3 -c US -X >> channels.conf     (note: command and pkg-name are different) (output below)
			(options: -ft = DVB-T,  -A 2 = cable,  -t 3 = slowest tuning timeout, -c = country, -X = output format)
	w_scan version 20111203 (compiled for DVB API 5.4)
	using settings for UNITED STATES
	ATSC
	QAM US/CA
	frontend_type ATSC, channellist 2
	output format czap/tzap/szap/xine
	WARNING: could not guess your codepage. Falling back to 'UTF-8'
	output charset 'UTF-8', use -C <charset> to override
	Info: using DVB adapter auto detection.
		/dev/dvb/adapter0/frontend0 -> ATSC "LG Electronics LGDT3305 VSB/QAM Frontend": good :-)
	Using ATSC frontend (adapter /dev/dvb/adapter0/frontend0)
	-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
	Using DVB API 5.4
	frontend 'LG Electronics LGDT3305 VSB/QAM Frontend' supports
	INVERSION_AUTO
	8VSB
	QAM_64
	QAM_256
	FREQ (54.00MHz ... 858.00MHz)
	-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
	57000: QAM256(time: 00:00) 
	63000: QAM256(time: 00:02) 
	69000: QAM256(time: 00:05) 
	79000: QAM256(time: 00:07) 
	85000: QAM256(time: 00:10) 
	177000: QAM256(time: 00:13) 
	183000: QAM256(time: 00:15) 
	189000: QAM256(time: 00:18) 
	195000: QAM256(time: 00:20) 
	201000: QAM256(time: 00:23) 
	207000: QAM256(time: 00:26) 
	213000: QAM256(time: 00:28) 
	123000: QAM256(time: 00:31) 
	123012: QAM256(time: 00:33) 
	129000: QAM256(time: 00:36) 
	129012: QAM256(time: 00:38) 
	135000: QAM256(time: 00:41) 
	.
	.
	.
	807000: QAM256(time: 06:41) 
	813000: QAM256(time: 06:44) 
	819000: QAM256(time: 06:46) 
	825000: QAM256(time: 06:49) 
	831000: QAM256(time: 06:51) 
	837000: QAM256(time: 06:54) 
	843000: QAM256(time: 06:56) 
	849000: QAM256(time: 06:59) 
	tune to: QAM256   f=153000 kHz 
	(time: 07:02) Info: VCT(cable) filter timeout
	tune to: QAM256   f=111000 kHz 
	(time: 07:08) Info: VCT(cable) filter timeout
	tune to: QAM256   f=117000 kHz 
	(time: 07:15) Info: VCT(cable) filter timeout
	tune to: QAM256   f=693000 kHz 
	(time: 07:23) Info: VCT(cable) filter timeout
	dumping lists (7 services)
	Done.

w_scan -fc -A2 -t3 -c US -X >> channels.conf
	(option: -fc = DVB-c. Note this produced similiar results as with option -ft  =  no usable TV channels)
	
	.
	.
	.
	849000: QAM256(time: 06:56) 
	tune to: QAM256   f=153000 kHz 
	(time: 06:58) ----------no signal----------
	tune to: QAM256   f=153000 kHz  (no signal)
	(time: 07:01) ----------no signal----------
	tune to: QAM256   f=111000 kHz 
	(time: 07:04) ----------no signal----------
	tune to: QAM256   f=111000 kHz  (no signal)
	(time: 07:07) ----------no signal----------
	tune to: QAM256   f=117000 kHz 
	(time: 07:11) ----------no signal----------
	tune to: QAM256   f=117000 kHz  (no signal)
	(time: 07:14) ----------no signal----------
	tune to: QAM256   f=693000 kHz 
	(time: 07:17) ----------no signal----------
	tune to: QAM256   f=693000 kHz  (no signal)
	(time: 07:20) ----------no signal----------

	ERROR: Sorry - i couldn't get any working frequency/transponder
	 Nothing to scan!!

```

 reviewed these URLS:
[http://www.linuxtv.org/wiki/index.ph...WinTV-HVR-1250](http://www.linuxtv.org/wiki/index.ph...WinTV-HVR-1250)
[http://ubuntuforums.org/showthread.php?t=1669420](http://ubuntuforums.org/showthread.php?t=1669420)
[http://ubuntuforums.org/showthread.php?t=1648472](http://ubuntuforums.org/showthread.php?t=1648472)
[http://ubuntuforums.org/showthread.php?t=1573600](http://ubuntuforums.org/showthread.php?t=1573600)
[http://www.mythtv.org/wiki/Adding_Di..._--_USA/Canada](http://www.mythtv.org/wiki/Adding_Di..._--_USA/Canada))

---

### Post by nickrout on 2012-05-29
Define "doesn't work".

I assume you are still using your old database. Why do you need to "find channels"?

---

### Post by nhtrader on 2012-05-29
Nickrout, No I am not. I did a complete fresh install. Nothing left from any previous installation. No files; no data; no recordings; nothing. As for it doesn't work. I couldn't get any working channels after a channel scan. And as was reported, I even tried various methods of scanning.


However, in the mean time I've been at it slugging away and I finally fixed it through trial and error.


Basically I tried different card numbers from the following list:
```

Card Listing within CX23885
	11.605378] cx23885[0]: card=0 -> UNKNOWN/GENERIC 
	[ 11.605379] cx23885[0]: card=1 -> Hauppauge WinTV-HVR1800lp 
	[ 11.605381] cx23885[0]: card=2 -> Hauppauge WinTV-HVR1800 
	[ 11.605382] cx23885[0]: card=3 -> Hauppauge WinTV-HVR1250 
	[ 11.605383] cx23885[0]: card=4 -> DViCO FusionHDTV5 Express 
	[ 11.605384] cx23885[0]: card=5 -> Hauppauge WinTV-HVR1500Q 
	[ 11.605385] cx23885[0]: card=6 -> Hauppauge WinTV-HVR1500 
	[ 11.605387] cx23885[0]: card=7 -> Hauppauge WinTV-HVR1200 
	[ 11.605388] cx23885[0]: card=8 -> Hauppauge WinTV-HVR1700 
	[ 11.605389] cx23885[0]: card=9 -> Hauppauge WinTV-HVR1400 
	[ 11.605390] cx23885[0]: card=10 -> DViCO FusionHDTV7 Dual Express 
	[ 11.605391] cx23885[0]: card=11 -> DViCO FusionHDTV DVB-T Dual Express 
	[ 11.605393] cx23885[0]: card=12 -> Leadtek Winfast PxDVR3200 H 
	[ 11.605394] cx23885[0]: card=13 -> Compro VideoMate E650F 
	[ 11.605395] cx23885[0]: card=14 -> TurboSight TBS 6920 
	[ 11.605396] cx23885[0]: card=15 -> TeVii S470 
	[ 11.605397] cx23885[0]: card=16 -> DVBWorld DVB-S2 2005 
	[ 11.605399] cx23885[0]: card=17 -> NetUP Dual DVB-S2 CI 
	[ 11.605400] cx23885[0]: card=18 -> Hauppauge WinTV-HVR1270 
	[ 11.605401] cx23885[0]: card=19 -> Hauppauge WinTV-HVR1275 
	[ 11.605402] cx23885[0]: card=20 -> Hauppauge WinTV-HVR1255 
	[ 11.605403] cx23885[0]: card=21 -> Hauppauge WinTV-HVR1210 
	[ 11.605405] cx23885[0]: card=22 -> Mygica X8506 DMB-TH 
	[ 11.605406] cx23885[0]: card=23 -> Magic-Pro ProHDTV Extreme 2 
	[ 11.605407] cx23885[0]: card=24 -> Hauppauge WinTV-HVR1850 
	[ 11.605408] cx23885[0]: card=25 -> Compro VideoMate E800


```

The number that worked for me was 19.

So I then created a file and inserted two lines:

```

sudo su
pico /etc/modprobe.d/cx23885.conf
	options cx23885 card=19
	options CORE_cx23885[0]_dvb adapter_nr=0


```


Then Shutdown/reboot 
Then checked system response with commands:
```

sudo su
dmesg|grep cx23885
[   12.863705] cx23885 driver version 0.0.3 loaded
[   12.877992] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.878164] CORE cx23885[0]: subsystem: 0070:2211, board: Hauppauge WinTV-HVR1275 [card=19,insmod option]
[   13.025350] cx23885[0]: hauppauge eeprom: model=22111
[   13.025352] cx23885_dvb_register() allocating 1 frontend(s)
[   13.025355] cx23885[0]: cx23885 based dvb card
[   13.304723] DVB: registering new adapter (cx23885[0])
[   13.305056] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   13.305061] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfd600000
[   13.305069] cx23885 0000:02:00.0: setting latency timer to 64


```

Notice, there are no errors.

Then used MythTV Backend Setup.

2. Capture Cards - checked to make sure that an adapter was available
Also changed Signal Timeout to 4000msec, Tuning Timeout to 4000msec
Then within Recording Options I changed DVB tuning delay to 2000msec.
I introduced more delays so that it would have a better chance of finding channels.

5. Input Connections - rescanned channels and found 20+

Then entered MythTV Frontend and watched TV for the first time after the fresh install of v0.25 (12.04 64bit).


In summary, why was it necessary to use card=19 rather than the autodetected card of 18, I don't know. Plus, why didn't card=3 work which is an exact match to the HVR-1250? 

Clearly something is still wrong with the CX23885 module. 

This was quite frustrating b/c there is are many older threads regurgitating the same information which required installing many new packages (which ended up being useless and a waste of time) or it went down the rabbit hole of doing the most complicated and advanced procedures which involved patching code. Both of which it turns out, are unnecessary.

I still would like to know if there is a better way to diagnose this type of problem. There must be a better way than to hack away using trial and error.

---

### Post by nickrout on 2012-05-29
Perhaps try asking hauppauge why they ship cards with the same VendorID : ProductID but with different chipsets inside. I think that is probably the key to it.

---

### Post by Quadari on 2012-05-31
Very interesting....I wonder if this is what happened to me as well.  I have a Hauppage HVR-1600 which worked great under 0.24.  Then I upgraded to 0.25 and I suddenly mostly lost the ability to tune to a few channels.  (Some worked, some mysteriously didn't.)  It has been very annoying, since you don't expect to lose functionality when you upgrade.

I notice that the 1600 uses a different driver, the CX23418.

Where is the file located with the list of card types for your driver?  I might try playing with mine like you did to see if I can get it to tune to my channels.

Thanks.

---

### Post by nhtrader on 2012-06-11
> **Quadari said:**
> Very interesting....I wonder if this is what happened to me as well.  I have a Hauppage HVR-1600 which worked great under 0.24.  Then I upgraded to 0.25 and I suddenly mostly lost the ability to tune to a few channels.  (Some worked, some mysteriously didn't.)  It has been very annoying, since you don't expect to lose functionality when you upgrade.

I notice that the 1600 uses a different driver, the CX23418.

Where is the file located with the list of card types for your driver?  I might try playing with mine like you did to see if I can get it to tune to my channels.

Thanks.

I think the command was ...
sudo su
dmesg|grep cx23885

However, I think the list only appears when your system installation can't recognize the card. 

Hope this helps.

---

### Post by nickrout on 2012-06-11
> **nhtrader said:**
> I think the command was ...
sudo su
dmesg|grep cx23885

However, I think the list only appears when your system installation can't recognize the card. 

Hope this helps.

Please stop spreading nonsense like that. You do not need to be root to run dmesg. The sudo su step is unnecessary and potentially dangerous.

Even if root permissions were needed you would run sudo dmesg|grep cx23885

---

