---
title: "Problems changing mac address"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by sky5564 on 2011-11-23
Cant seem to change the mac address on my network card

lscpi -vv

```
Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
	Subsystem: Foxconn International, Inc. Device e021
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at d0100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=2 PME-
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
		Address: 0000000000000000  Data: 0000
	Capabilities: [d0] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
			ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <64us
			ClockPM+ Surprise- LLActRep+ BwNot-
		LnkCtl:	ASPM L0s L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive+ BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap+ CGenEn- ChkCap+ ChkEn-
	Capabilities: [13c v1] Virtual Channel
		Caps:	LPEVC=0 RefClk=100ns PATEntryBits=1
		Arb:	Fixed- WRR32- WRR64- WRR128-
		Ctrl:	ArbSelect=Fixed
		Status:	InProgress-
		VC0:	Caps:	PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
			Arb:	Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
			Ctrl:	Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
			Status:	NegoPending- InProgress-
	Capabilities: [160 v1] Device Serial Number xx-xx-xx-xx-xx-xx
	Capabilities: [16c v1] Power Budgeting <?>
	Kernel driver in use: brcmsmac
	Kernel modules: wl, brcmsmac

```

I enter in the mac address i want to spoof in edit network connections but then it wont let me connect to the router, i run ifconfig and it show that the mac has in fact been spoofed but something with the mac spoofing causes the network card to not be able to connect.

I have even tried using the macchanger tool package but it still wont connect.

Anyone have any problems with this?

---

### Post by sky5564 on 2011-11-24
Bumpity bump bump bump.

---

### Post by Robbo85 on 2011-11-25
What do you get in dmesg and tail /var/log/daemon ?

Also, could this not be your router rejecting your MAC address. Lots of routers you need to register your MAC address in order to connect. Try logging into your router and checking this.

---

### Post by sky5564 on 2011-11-26
> **Robbo85 said:**
> What do you get in dmesg and tail /var/log/daemon ?

Also, could this not be your router rejecting your MAC address. Lots of routers you need to register your MAC address in order to connect. Try logging into your router and checking this.

Nothing unsual in dmesg but there is some errors showing in the syslog file.

```
Nov 26 00:18:30 laptop avahi-daemon[547]: Withdrawing address record for fe80::9200:4eff:fe3f:c339 on wlan0.
Nov 26 00:18:30 laptop NetworkManager[723]: <info> (wlan0): set MAC address to 00:11:22:33:44:55
Nov 26 00:18:30 laptop kernel: [12113.078722] ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
Nov 26 00:18:30 laptop kernel: [12113.078738] ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
Nov 26 00:18:30 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 26 00:18:30 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 26 00:18:30 laptop kernel: [12113.096051] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
Nov 26 00:18:30 laptop kernel: [12113.097401] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 26 00:18:30 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 26 00:18:30 laptop NetworkManager[723]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 26 00:18:30 laptop NetworkManager[723]: <info> Activation (wlan0/wireless): connection 'Higdon ' has security, and secrets exist.  No new secrets needed.
Nov 26 00:18:30 laptop NetworkManager[723]: <info> Config: added 'ssid' value 'Higdon '
Nov 26 00:18:30 laptop NetworkManager[723]: <info> Config: added 'scan_ssid' value '1'
Nov 26 00:18:30 laptop NetworkManager[723]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 26 00:18:30 laptop NetworkManager[723]: <info> Config: added 'psk' value '<omitted>'
Nov 26 00:18:30 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 26 00:18:30 laptop NetworkManager[723]: <info> Config: set interface ap_scan to 1
Nov 26 00:18:30 laptop NetworkManager[723]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 26 00:18:30 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:18:30 laptop kernel: [12113.835641] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:18:30 laptop NetworkManager[723]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 26 00:18:31 laptop kernel: [12114.032212] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:18:31 laptop kernel: [12114.232283] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:18:31 laptop kernel: [12114.432299] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:18:37 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:18:37 laptop kernel: [12120.090909] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:18:37 laptop kernel: [12120.288275] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:18:37 laptop kernel: [12120.488305] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:18:37 laptop kernel: [12120.688303] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:18:43 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:18:43 laptop kernel: [12126.352291] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:18:43 laptop kernel: [12126.552245] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:18:43 laptop kernel: [12126.752313] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:18:43 laptop kernel: [12126.952296] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:18:49 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:18:49 laptop kernel: [12132.602436] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:18:49 laptop kernel: [12132.800297] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:18:50 laptop kernel: [12133.000290] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:18:50 laptop kernel: [12133.200279] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:18:55 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:18:55 laptop kernel: [12138.855489] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:18:56 laptop kernel: [12139.052452] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:18:56 laptop kernel: [12139.252302] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:18:56 laptop kernel: [12139.452300] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:19:02 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:19:02 laptop kernel: [12145.124485] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:19:02 laptop kernel: [12145.324152] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:19:02 laptop kernel: [12145.528249] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:19:02 laptop kernel: [12145.728252] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:19:08 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:19:08 laptop kernel: [12151.400170] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:19:08 laptop kernel: [12151.600273] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:19:08 laptop kernel: [12151.800169] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:19:09 laptop kernel: [12152.000286] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:19:14 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:19:14 laptop kernel: [12157.650275] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:19:14 laptop kernel: [12157.848322] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:19:15 laptop kernel: [12158.048159] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:19:15 laptop kernel: [12158.248187] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:19:20 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:19:20 laptop kernel: [12163.906125] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:19:21 laptop kernel: [12164.104251] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:19:21 laptop kernel: [12164.304190] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:19:21 laptop kernel: [12164.504130] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:19:27 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:19:27 laptop kernel: [12170.154304] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:19:27 laptop kernel: [12170.352290] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:19:27 laptop kernel: [12170.552265] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:19:27 laptop kernel: [12170.752172] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:19:30 laptop NetworkManager[723]: <warn> Activation (wlan0/wireless): association took too long.
Nov 26 00:19:30 laptop NetworkManager[723]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 26 00:19:30 laptop NetworkManager[723]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov 26 00:19:30 laptop NetworkManager[723]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 26 00:19:30 laptop NetworkManager[723]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 26 00:19:40 laptop NetworkManager[723]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 26 00:19:40 laptop NetworkManager[723]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 26 00:19:40 laptop NetworkManager[723]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Activation (wlan0/wireless): connection 'Higdon ' has security, and secrets exist.  No new secrets needed.
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Config: added 'ssid' value 'Higdon '
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Config: added 'scan_ssid' value '1'
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Config: added 'psk' value '<omitted>'
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 26 00:19:40 laptop NetworkManager[723]: <info> Config: set interface ap_scan to 1
Nov 26 00:19:40 laptop NetworkManager[723]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 26 00:19:40 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:19:40 laptop kernel: [12183.948128] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:19:40 laptop NetworkManager[723]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 26 00:19:41 laptop kernel: [12184.148277] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:19:41 laptop kernel: [12184.348250] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:19:41 laptop kernel: [12184.548102] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:19:47 laptop kernel: [12190.207227] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:19:47 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:19:47 laptop kernel: [12190.404214] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:19:47 laptop kernel: [12190.604134] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:19:47 laptop kernel: [12190.804344] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:19:53 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:19:53 laptop kernel: [12196.464785] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:19:53 laptop kernel: [12196.665506] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:19:53 laptop kernel: [12196.864324] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:19:54 laptop kernel: [12197.064063] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:19:59 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:19:59 laptop kernel: [12202.732908] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:19:59 laptop kernel: [12202.932173] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:20:00 laptop kernel: [12203.132085] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:20:00 laptop kernel: [12203.332097] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:20:05 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:20:06 laptop kernel: [12208.996366] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:20:06 laptop kernel: [12209.196087] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:20:06 laptop kernel: [12209.396160] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:20:06 laptop kernel: [12209.596096] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:20:12 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:20:12 laptop kernel: [12215.262235] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:20:12 laptop kernel: [12215.460286] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:20:12 laptop kernel: [12215.660154] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:20:12 laptop kernel: [12215.864170] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:20:18 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:20:18 laptop kernel: [12221.526126] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:20:18 laptop kernel: [12221.724179] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:20:18 laptop kernel: [12221.924172] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:20:19 laptop kernel: [12222.124130] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:20:24 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:20:24 laptop kernel: [12227.786224] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:20:24 laptop kernel: [12227.984132] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:20:25 laptop kernel: [12228.184146] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:20:25 laptop kernel: [12228.384144] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:20:31 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:20:31 laptop kernel: [12234.050863] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:20:31 laptop kernel: [12234.248262] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:20:31 laptop kernel: [12234.448259] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:20:31 laptop kernel: [12234.648256] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:20:37 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:20:37 laptop kernel: [12240.302092] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:20:37 laptop kernel: [12240.500194] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:20:37 laptop kernel: [12240.700076] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:20:37 laptop kernel: [12240.900280] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:20:40 laptop NetworkManager[723]: <warn> Activation (wlan0/wireless): association took too long.
Nov 26 00:20:40 laptop NetworkManager[723]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 26 00:20:40 laptop NetworkManager[723]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov 26 00:20:40 laptop NetworkManager[723]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 26 00:20:40 laptop NetworkManager[723]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 26 00:20:44 laptop NetworkManager[723]: <warn> No agents were available for this request.
Nov 26 00:20:44 laptop NetworkManager[723]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Nov 26 00:20:44 laptop NetworkManager[723]: <warn> Activation (wlan0) failed for access point (Higdon )
Nov 26 00:20:44 laptop NetworkManager[723]: <info> Marking connection 'Higdon ' invalid.
Nov 26 00:20:44 laptop NetworkManager[723]: <warn> Activation (wlan0) failed.
Nov 26 00:20:44 laptop NetworkManager[723]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 26 00:20:44 laptop NetworkManager[723]: <info> (wlan0): deactivating device (reason 'none') [0]
Nov 26 00:20:44 laptop NetworkManager[723]: <info> (wlan0): reset MAC address to 90:xx:xx:xx:xx:xx
Nov 26 00:20:44 laptop kernel: [12247.130287] ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
Nov 26 00:20:44 laptop kernel: [12247.130304] ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
Nov 26 00:20:44 laptop kernel: [12247.143782] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
Nov 26 00:20:44 laptop kernel: [12247.153547] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 26 00:28:52 laptop sudo: pam_ecryptfs: pam_sm_authenticate: /home/skilo is already mounted
Nov 26 00:29:22 laptop kernel: [12765.155477] ieee80211 phy0: wl_ops_config: change monitor mode: false (implement)
Nov 26 00:29:22 laptop kernel: [12765.155496] ieee80211 phy0: wl_ops_config: change power-save mode: false (implement)
Nov 26 00:29:22 laptop kernel: [12765.169088] ieee80211 phy0: wl_ops_bss_info_changed: qos enabled: false (implement)
Nov 26 00:29:22 laptop kernel: [12765.170922] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Activation (wlan0) starting connection 'Higdon '
Nov 26 00:29:51 laptop NetworkManager[723]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 26 00:29:51 laptop NetworkManager[723]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Activation (wlan0/wireless): connection 'Higdon ' has security, and secrets exist.  No new secrets needed.
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Config: added 'ssid' value 'Higdon '
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Config: added 'scan_ssid' value '1'
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Config: added 'psk' value '<omitted>'
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 26 00:29:51 laptop NetworkManager[723]: <info> Config: set interface ap_scan to 1
Nov 26 00:29:51 laptop NetworkManager[723]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Nov 26 00:29:51 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:29:51 laptop kernel: [12794.842290] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:29:51 laptop NetworkManager[723]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 26 00:29:52 laptop kernel: [12795.040334] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:29:52 laptop kernel: [12795.240255] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:29:52 laptop kernel: [12795.440252] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:29:58 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:29:58 laptop kernel: [12801.090227] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:29:58 laptop kernel: [12801.288169] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:29:58 laptop kernel: [12801.488270] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:29:58 laptop kernel: [12801.688300] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:30:01 laptop CRON[3763]: (root) CMD (/usr/local/bin/msfupdate nowait --config-dir=/opt/framework-4.0.0/config/svn >> /var/log/msfupdate.log 2>&1)
Nov 26 00:30:04 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:30:04 laptop kernel: [12807.350530] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:30:04 laptop kernel: [12807.548224] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:30:04 laptop kernel: [12807.750244] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:30:04 laptop kernel: [12807.948248] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:30:10 laptop kernel: [12813.611107] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:30:10 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:30:10 laptop kernel: [12813.808149] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:30:11 laptop kernel: [12814.008064] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:30:11 laptop kernel: [12814.208118] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:30:16 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:30:16 laptop kernel: [12819.874128] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:30:17 laptop kernel: [12820.072093] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:30:17 laptop kernel: [12820.272250] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:30:17 laptop kernel: [12820.472095] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:30:23 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:30:23 laptop kernel: [12826.141160] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:30:23 laptop kernel: [12826.340197] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:30:23 laptop kernel: [12826.540294] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:30:23 laptop kernel: [12826.740176] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:30:29 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:30:29 laptop kernel: [12832.390272] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:30:29 laptop kernel: [12832.588282] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:30:29 laptop kernel: [12832.788267] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:30:30 laptop kernel: [12832.988176] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:30:35 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:30:35 laptop kernel: [12838.639850] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:30:35 laptop kernel: [12838.836091] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:30:36 laptop kernel: [12839.036170] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:30:36 laptop kernel: [12839.236148] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:30:41 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:30:41 laptop kernel: [12844.894407] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:30:42 laptop kernel: [12845.092276] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:30:42 laptop kernel: [12845.292289] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:30:42 laptop kernel: [12845.492291] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:30:48 laptop wpa_supplicant[1056]: Trying to authenticate with e0:91:53:0c:2d:51 (SSID='Higdon ' freq=2437 MHz)
Nov 26 00:30:48 laptop kernel: [12851.152368] wlan0: authenticate with e0:91:53:0c:2d:51 (try 1)
Nov 26 00:30:48 laptop kernel: [12851.352333] wlan0: authenticate with e0:91:53:0c:2d:51 (try 2)
Nov 26 00:30:48 laptop kernel: [12851.552280] wlan0: authenticate with e0:91:53:0c:2d:51 (try 3)
Nov 26 00:30:48 laptop kernel: [12851.752287] wlan0: authentication with e0:91:53:0c:2d:51 timed out
Nov 26 00:30:51 laptop NetworkManager[723]: <warn> Activation (wlan
```

I used sudo ifconfig wlan0 hw ether 00:11:22:33:44:55

To set the mac address manually, This worked and the mac address sticks enven after trying to connect but the only problem is it never connects.

What do you make of the log?

I checked my router and it is not the problem, mac filtering is disabled

---

### Post by sky5564 on 2011-11-27
Bumpity bump bump

---

### Post by sky5564 on 2011-11-28
I will bump this thread for the next 30 years if i dont get any replies...

---

### Post by pod787 on 2011-12-10
I've got the same hardware and yes, I can change the mac but cannot connect after I do so. Will keep looking at why this is so, for the mean time maybe try wicd instead of network manager to rule out nm.

---

