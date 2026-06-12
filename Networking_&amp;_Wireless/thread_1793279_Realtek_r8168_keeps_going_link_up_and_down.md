---
title: "Realtek r8168 keeps going link up and down"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by tama on 2011-06-29
After compiling the Realtek drivers from their page (ver 8.024), installing the module, blacklisting r8169 and updating the initramfs, I still can't get the network card working.

The card is listed in lshw as RTL8111/8168B PCI Express Gigabit Ethernet controller.

lsmod shows only r8168.

dmesg keeps spitting once and again, every second or so the following:
```
[ 1293.452274] r8168: eth0: link up
[ 1294.449785] r8168: eth0: link down
[ 1295.447269] r8168: eth0: link up
[ 1296.444759] r8168: eth0: link down
```

I've tried both DHCP and static address, with no success...

Do you have any hint on what should I try?

Thanks!

---

### Post by poolet on 2011-07-02
As I mention in other thread, try to blacklist the r8168 mod and load r8169 to see what happen... Also if your using network manager remove it and download and install wicd.....

---

### Post by chili555 on 2011-07-02
> **poolet said:**
> As I mention in other thread, try to blacklist the r8168 mod and load r8169 to see what happen... Also if your using network manager remove it and download and install wicd.....```
$ modinfo r8168
ERROR: modinfo: could not find module r8168
```Chili is all like :confused: :confused: :confused:

---

### Post by dsluser on 2011-07-02
This sounds similiar to something I'm currently experiencing. Can you 

sudo modprobe -l | grep r81 

and post the results here?

also 

lsmod | grep r81

cat /etc/modprobe.d/blacklist.conf

Cheers

---

### Post by tama on 2011-07-05
It's working now, I don't know why...

Last thing I did was update packages (and kernel) and reboot and it was working, but I'm not sure if it's only the kernel or there's something else. I just tried too many things...

In case it's of any help:
> $ sudo modprobe -l |grep r81
kernel/drivers/staging/rtl8187se/r8187se.ko
kernel/drivers/staging/rtl8192u/r8192u_usb.ko
kernel/drivers/staging/rtl8192e/r8192e_pci.ko
kernel/ubuntu/rtl8192se/r8192se_pci.ko
kernel/drivers/net/r8168.ko
and:
> $ lsmod |grep r81
r8168                 181357  0

r8169 never seemed to work.

Cheers.

---

### Post by andrewthomas on 2011-07-18
I have had this motherboard for over two years without a single problem with the r8169 kernel driver.

```

2:00.0 **Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)**
	Subsystem: Micro-Star International Co., Ltd. Device 388c
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 43
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] Vital Product Data
		Unknown small resource type 05, will not decode more.
	Capabilities: [50] MSI: Enable+ Count=1/2 Maskable- 64bit+
		Address: 00000000fee0f00c  Data: 4169
	Capabilities: [60] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 1024 bytes, PhantFunc 0, Latency L0s <128ns, L1 unlimited
			ExtTag+ AttnBtn+ AttnInd+ PwrInd+ RBE- FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
			MaxPayload 128 bytes, MaxReadReq 4096 bytes
		DevSta:	CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 unlimited, L1 unlimited
			ClockPM- Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
	Capabilities: [84] Vendor Specific Information: Len=4c <?>
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq+ ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		AERCap:	First Error Pointer: 14, GenCap- CGenEn- ChkCap- ChkEn-
	Capabilities: [12c v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Capabilities: [148 v1] Device Serial Number 01-00-00-00-68-4c-e0-00
	Capabilities: [154 v1] Power Budgeting <?>
	**Kernel driver in use: r8169**

```

---

### Post by dsluser on 2011-09-20
My problem was resolved by replacing my router, seems zyxel p-660hw-T1 and Linux don't mix very well

---

### Post by ionplay on 2012-03-30
how can the problem be resolved by changing the router/hub/switch?

---

### Post by ionplay on 2012-03-30
> **poolet said:**
> As I mention in other thread, try to blacklist the r8168 mod and load r8169 to see what happen... Also if your using network manager remove it and download and install wicd.....

I have some 8.0.4 machines running (cant upgrade to 10 yet on those machines)
and by default had the r8169 - but nothing worked

and on another thread found others with same issue and recommended fix was to uninstall r8169 in favour of r8168; also with recommendation from realtek to ditch r8169 driver

r8168 works for about 2 minutes after restarting the network
/etc/init.d/networking restart


normally realtek chips/drivers on linux have been very robust for almost 20 years - having a hard time rationalizing this inconsistency now.

---

### Post by ubume2 on 2012-03-30
This is an old thread.  I have a new computer. Started having problems ethernet going up and down.  Running 10.04 and pae kernel.  Solved by installing r8168.

Installed build essential and followed this sequence:

Re: Set installed Realtek drivers permanently
Blacklist the wrong one:

Code:

echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rf r8169
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u

---

### Post by ionplay on 2012-03-30
Ubuntu 8.0.4 did the following
apt-get update
apt-get dist-upgrade
*using r8168

works fine now

my 10.0.4 does not have this issue

something needed to be updated to work properly with the r8168 driver - unfortunately I have no idea what specifically needed to be updated

---

