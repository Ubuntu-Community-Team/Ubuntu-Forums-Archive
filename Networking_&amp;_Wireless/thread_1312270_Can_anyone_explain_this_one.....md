---
title: "Can anyone explain this one...."
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by bpd115 on 2009-11-03
I have an MSI Wind with an Atheros 5001 card installed (ripped from a 1st Gen Macbook Pro)

Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Apple Computer Inc. Device 0086
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at dfc00000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k


I've installed Netbook Remix 9.10 and also installed the linux backports modules wireless karmic generic package.

The card picks up my wireless network fine (I have an Airport Extreme base station and an Airport express extended via WDS).  When I try and connect, using Network Manager, It simply will not authenticate and asks for my password over and over. I'm using WPA2. 

I've been getting online via Ethernet sharing from my Macbook Pro.  

I wanted to see if I could connect to an open network, I decide to create a computer to computer wireless network on my Macbook Pro.  I create an open access point and check my Wind....Lo and Behold, it's CONNECTED TO MY WPA Airport network (posting this from it right now).

If I disable the Open Access Point created on my Macbook Pro, I'll start to drop packets and the connection will die.

I'm at a loss.

---

### Post by cybergalvez on 2009-11-03
try using wicd, that seems to work better then network manager, at least it works better for me

---

### Post by bpd115 on 2009-11-05
I installed Wicd and updated it to 1.6.2.2

Same behavior.

Wicd will connect fine as long as I have an unprotected network near by.  I started a ping to yahoo.com and was getting about 103 ms in my replies.  I then turned the wireless on my Macbook Pro off, (eliminating the open network) and my ping replies are now at 2000-4000 ms.

I'm still "connected" to my WPA2 network, but I can't browse....

---

