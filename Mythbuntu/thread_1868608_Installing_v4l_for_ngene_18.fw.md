---
title: "Installing v4l for ngene_18.fw"
date: 2011-10-24
forum: Mythbuntu
---

### Post by TwPlo on 2011-10-24
make CineS2_Solved
make[2] error 2 Read last post.
______________________________

I installed mythbuntu 64 bit .
A digitaldevices Cines2 card is installed.
This device works under windows, but want to leave the windows path completely.

Edit : Mythbuntu 11.10



Compiling gives problems.


First :
lspci -vvvnn results

```
01:00.0 Multimedia video controller [0400]: Micronas Semiconductor Holding AG nGene PCI-Express Multimedia Controller [18c3:0720] (rev 01)
    Subsystem: Micronas Semiconductor Holding AG Device [18c3:dd20]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 42
    Region 0: Memory at fea10000 (32-bit, non-prefetchable) [size=64K]
    Region 1: Memory at fea00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ngene
    Kernel modules: ngene

03:00.0 Multimedia video controller [0400]: Micronas Semiconductor Holding AG nGene PCI-Express Multimedia Controller [18c3:0720]
    Subsystem: Micronas Semiconductor Holding AG Device [18c3:abc4]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 43
    Region 0: Memory at fe910000 (32-bit, non-prefetchable) [size=64K]
    Region 1: Memory at fe900000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ngene
    Kernel modules: ngene
```Because of the device 18c3:dd00, I download ngene_18.fw

Copying the firmware.
but Building v4l-dvb fails.

```
Make[3]:*** [home/dvb/v4l-dvb/tuner-xc2028.o] Error 1
Make[2]:*** [_module_/home/dvb/v4l-dvb/4vl] Error 2
Make[1] *** [default] Error 2
make: *** [all] Error 2
```Linux headers installed, automake installed, autoconf installed.

Did I miss something?

Note : Capabilities: <access denied>

Eh? Access Denied?

I'm sure that I did miss something but what is another question .

Any hints?

---

### Post by TwPlo on 2011-10-26
I re-installed ubuntu 11.10, this time amd64 version (64bit)
Kernel 3.0


I follow the info found on [http://linuxtv.org/wiki/index.php/Linux4Media_cineS2_DVB-S2_Twin_Tuner](http://linuxtv.org/wiki/index.php/Linux4Media_cineS2_DVB-S2_Twin_Tuner)

My lspci log:

First tuner :
```

01:00.0 Multimedia video controller [0400]: Micronas Semiconductor Holding AG nGene PCI-Express Multimedia Controller [18c3:0720] (rev 01)
    Subsystem: Micronas Semiconductor Holding AG Device [18c3:dd20]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fea10000 (32-bit, non-prefetchable) [size=64K]
    Region 1: Memory at fea00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: ngene
```

Quote from linuxtv.org:

```
03:00.0 Multimedia video controller [0400]: Micronas Semiconductor Holding AG Device [18c3:0720]  (rev 01) 	Subsystem: Micronas Semiconductor Holding AG Device [18c3:dd00] 	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR-  FastB2B- DisINTx- 	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR-   <PERR- INTx- 	Latency: 0, Cache Line Size: 32 bytes 	Interrupt: pin A routed to IRQ 10 	Region 0: Memory at fddf0000 (32-bit, non-prefetchable) [size=64K] 	Region 1: Memory at fdde0000 (64-bit, non-prefetchable) [size=64K] 	Capabilities: [40] Power Management version 2 		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-) 		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME- 	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+ 		Address: 0000000000000000  Data: 0000 	Capabilities: [58] Express (v1) Endpoint, MSI 00 		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us 			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset- 		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported- 			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ 			MaxPayload 128 bytes, MaxReadReq 512 bytes 		DevSta:	CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend- 		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 unlimited, L1  unlimited 			ClockPM- Surprise- LLActRep- BwNot- 		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+ 			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt- 		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt- 	Capabilities: [100] Device Serial Number 00-00-00-00-00-00-00-00 	Capabilities: [400] Virtual Channel <?>
```


Tuner 2: (or vice versa)

My log:
```

03:00.0 Multimedia video controller [0400]: Micronas Semiconductor Holding AG nGene PCI-Express Multimedia Controller [18c3:0720]
	Subsystem: Micronas Semiconductor Holding AG Device [18c3:abc4]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fe910000 (32-bit, non-prefetchable) [size=64K]
	Region 1: Memory at fe900000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ngene
```
LinuxTV :

```
02:00.0 Multimedia video controller [0400]: Micronas Semiconductor Holding AG Device [18c3:0720] 	Subsystem: Micronas Semiconductor Holding AG Device [18c3:abc4] 	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx- 	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+ 	Latency: 0, Cache Line Size: 32 bytes 	Interrupt: pin A routed to IRQ 16 	Region 0: Memory at fe8f0000 (32-bit, non-prefetchable) [size=64K] 	Region 1: Memory at fe8e0000 (64-bit, non-prefetchable) [size=64K] 	Capabilities: [40] Power Management version 2 		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-) 		Status: D0 PME-Enable- DSel=0 DScale=0 PME- 	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable- 		Address: 0000000000000000  Data: 0000 	Capabilities: [58] Express (v1) Endpoint, MSI 00 		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us 			ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset- 		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported- 			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ 			MaxPayload 128 bytes, MaxReadReq 512 bytes 		DevSta:	CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend- 		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 unlimited, L1 unlimited 			ClockPM- Suprise- LLActRep- BwNot- 		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk- 			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt- 		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt- 	Capabilities: [100] Device Serial Number 00-11-3c-20-07-00-00-00 	Capabilities: [400] Virtual Channel <?> 	Kernel driver in use: ngene 	Kernel modules: ngene

```

hmm, lots "options" not available.  The cine S2 runs fine on windoooos platform.
Tested that yesterday.

And ?? dd20 should have firmware ngene_18.fw
But abc4 the firmware ngene_15.fw

That sounds weird, one DVB card with different firmware.


Make error complete , except entering and leaving directory lines not included.
no problem with those.  
```
make -C /home/dvb/v4l
creating symbolic links...
make -C firmware prep
make -C firmware
make[2]: Nothing to be done for 'default'
Kernel build directory is /lib/modules/3.0.0-12-generic/build
make -C /lib/modules/3.0.0-12-generic/build SUBDIRS=/home/dvb/v4l-dvb/v4l CFLAGS="-I../linux/include -D__KERNEL__ -I/include -DEXPORT_SYMTAB" modules
CC [M] /home/dvb/v4l-dvb/v4l/tuner-xc2028.o
/home/dvb/v4l-dvb/v4l/tuner-xc2028.c: In function 'xc2028-set-params':
/home/dvb/v4l-dvb/v4l/tuner-xc2028.c:1178:5: error: 'T_DIGITAL_TV' undeclared (first use this in this function)
/home/dvb/v4l-dvb/v4l/tuner-xc2028.c:1178:5: note : each undeclared identifier is reported only once for each function it appears in
/home/dvb/v4l-dvb/v4l/tuner-xc2028.c:1179:1: warning: control reaches en of non-void function [-Wreturn-type]
make[3]:*** [/home/dvb/v4l-dvb/v4l/tuner-xc2028.o] Error 1
make[2]:*** [_module_/home/dvb/v4l-dvb/v4l] Error 2
make[1]:*** [default] Error 2
make: *** [all] Error 
```

Note: entering and leaving directory lines not included.
no problem with those.

---

### Post by TwPlo on 2011-10-26
hmm, still not enough information?
What is missing then?
so bump.

---

### Post by TwPlo on 2011-10-26
sorry but after 3 day of trying, I give up.
Back to windows.

Linux is not suitable for a htpc with a modern, wait, the cineS2 design is not so new anymore
dvb-s2 receiver.

Too much fiddling to get zero effect.
Back to windowsXP, cyberlink powerDVD and DVBviewer.

Let's say, I sure will not promote linux, no matter which distro  it may be.

Grr etc..

---

### Post by nickrout on 2011-10-26
Perhaps if you could provide a decent report and explain what you are doing and what is going on, someone could help.

In the meantime, you seem well suited to windows, do enjoy it won't you?

---

### Post by TwPlo on 2011-10-27
> hmm, still not enough information?
What is missing then?
so bump.

If there was not enough information  then someone could say what is still missing.


Was it not obvious:

I have a digitaldevices CineS2 which should be working under linux at least with newest kernels.

So, first lspci log:
Yes, cines23 detected but lspi gives less data then found on the linuxtv.org website.

```
Capabilities : <Acces Denied>
```

I make of this: ok, device found but suprise, may not be used.
But starting lspci as root same result.


The rest of the install fails after following the info on:
[http://linuxtv.org/wiki/index.php/Li...-S2_Twin_Tuner]("http://linuxtv.org/wiki/index.php/Linux4Media_cineS2_DVB-S2_Twin_Tuner")

So: v4l-dvb fails at make but perhaps for the same reason :
```
Capabilities : <Acces Denied>
``` < is a resonable message 

Als tested as root, same error.

No, I don't like windows at all, but at least it's a working solution 
Not something I can say on linux side, but I have installed another distro yesterday , centos after mythbuntu, ubuntu but at the point where it's centos or windows.

---

