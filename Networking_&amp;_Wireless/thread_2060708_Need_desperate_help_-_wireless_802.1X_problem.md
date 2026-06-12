---
title: "Need desperate help - wireless 802.1X problem"
date: 2012-09-20
forum: Networking &amp; Wireless
---

### Post by alperyilmaz on 2012-09-20
Hi, I need desparate help regarding my wireless connection problem. I cannot connect to my university's wireless network which uses WEP802.1X security. 
When I switch to Windows Vista, I can connect to university wireless network.
But when I use Ubuntu, I cannot connect.
Also, when I use Ubuntu, I can connect to other wireless networks either non-password-protected or WEP password protected networks. But I cannot connect to enterprise networks.

The problem seems not related to Ubuntu per se, but one of the network related packages (ie. wpa_supplicant, dhclient, etc).
I need help from an expert. I hope the right person reads this post and helps me.

I am in such a desparate situation, I am willing to pay (around $30) to whom suggesting the right solution. I live outside of USA, I can pay thru PayPal only. 

If you want me to perform tests or tasks please let me know.

Below are details regarding my system, the problem and my struggle.

### nm-applet settings (username, password not shown) ###
```

security: Dynamic WEP (802.1x) 
Authentication: PEAP 
CA certificate: None 
Peap version: Automatic 
Inner authentication: MSCHAPv2 
Username: USERNAME 
Password: PASSWORD

```

### system related information ###
```

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

$ uname -a
Linux dv7 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

$ iwconfig

wlan0     IEEE 802.11abgn  ESSID:"yildiz-net"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:25:46:83:90:80   
          Bit Rate=2 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

$ sudo lspci -vvv

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation WiFi Link 5100 AGN
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 48
	Region 0: Memory at d9000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee0100c  Data: 41b1
	Capabilities: [e0] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ FLReset-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <128ns, L1 <32us
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
	Capabilities: [140 v1] Device Serial Number 00-22-fa-ff-ff-d6-b4-ba
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

```

### dmesg ###
```


[143138.193079] wlan0: authenticate with 00:25:46:83:90:80 (try 1)
[143138.195833] wlan0: authenticated
[143138.196859] wlan0: associate with 00:25:46:83:90:80 (try 1)
[143138.199087] wlan0: RX ReassocResp from 00:25:46:83:90:80 (capab=0x431 status=0 aid=2)
[143138.199092] wlan0: associated
[143148.352026] wlan0: no IPv6 routers present
[143184.218453] wlan0: deauthenticating from 00:25:46:83:90:80 by local choice (reason=3)
[143184.280814] cfg80211: All devices are disconnected, going to restore regulatory settings
[143184.280821] cfg80211: Restoring regulatory settings
[143184.280849] cfg80211: Calling CRDA to update world regulatory domain
[143184.286035] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[143184.286041] cfg80211: World regulatory domain updated:
[143184.286044] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[143184.286048] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[143184.286052] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[143184.286056] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[143184.286059] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[143184.286063] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


```

### /var/log/syslog ###
```


Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) starting connection 'yildiz-net'
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40
 0]
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0/wireless): access point 'yildiz-net' has security, but sec
rets are required.
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0/wireless): connection 'yildiz-net' has security, and secrets exist.  No new secrets needed.
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Config: added 'ssid' value 'yildiz-net'
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Config: added 'scan_ssid' value '1'
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Config: added 'key_mgmt' value 'IEEE8021X'
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Config: added 'password' value '<omitted>'
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Config: added 'eap' value 'PEAP'
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Config: added 'fragment_size' value '1300'
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Config: added 'phase2' value 'auth=MSCHAPV2'
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Config: added 'identity' value 'USERNAME_NOT_SHOWN'
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 22 22:18:36 dv7 NetworkManager[4519]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Aug 22 22:18:36  NetworkManager[4519]: last message repeated 2 times
Aug 22 22:18:36 dv7 NetworkManager[4519]: <info> Config: set interface ap_scan to 1
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: Trying to authenticate with 00:25:46:83:90:80 (SSID='yildiz-net' freq=2412 MHz)
Aug 22 22:18:44 dv7 kernel: [145845.603199] wlan0: authenticate with 00:25:46:83:90:80 (try 1)
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: Trying to associate with 00:25:46:83:90:80 (SSID='yildiz-net' freq=2412 MHz)
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> (wlan0): supplicant interface state: scanning -> associating
Aug 22 22:18:44 dv7 kernel: [145845.604562] wlan0: authenticated
Aug 22 22:18:44 dv7 kernel: [145845.605831] wlan0: associate with 00:25:46:83:90:80 (try 1)
Aug 22 22:18:44 dv7 kernel: [145845.607779] wlan0: RX ReassocResp from 00:25:46:83:90:80 (capab=0x431 status=0 aid=2)
Aug 22 22:18:44 dv7 kernel: [145845.607784] wlan0: associated
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: Associated with 00:25:46:83:90:80
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: CTRL-EVENT-EAP-STARTED EAP authentication started
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> (wlan0): supplicant interface state: associating -> associated
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: CTRL-EVENT-EAP-PEER-CERT depth=1 subject='/C=TR/ST=Besiktas/L=Istanbul/O=Yildiz Technical University/OU=IT Center'
Aug 22 22:18:44  wpa_supplicant[4528]: last message repeated 2 times
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: CTRL-EVENT-EAP-PEER-CERT depth=0 subject='/C=TR/ST=Besiktas/L=Istanbul/O=Yildiz Technical University/OU=IT Center/CN=obelix'
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: CTRL-EVENT-EAP-PEER-CERT depth=0 subject='/C=TR/ST=Besiktas/L=Istanbul/O=Yildiz Technical University/OU=IT Center/CN=obelix'
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: EAP-MSCHAPV2: Authentication succeeded
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
Aug 22 22:18:44 dv7 wpa_supplicant[4528]: CTRL-EVENT-CONNECTED - Connection to 00:25:46:83:90:80 completed (reauth) [id=0 id_str=]
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> (wlan0): supplicant interface state: associated -> completed
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'yildiz-net'.
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> dhclient started with pid 4933
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> Activation (wlan0) Beginning IP6 addrconf.
Aug 22 22:18:44 dv7 avahi-daemon[1263]: Withdrawing address record for fe80::222:faff:fed6:b4ba on wlan0.
Aug 22 22:18:44 dv7 avahi-daemon[1263]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::222:faff:fed6:b4ba.
Aug 22 22:18:44 dv7 avahi-daemon[1263]: Interface wlan0.IPv6 no longer relevant for mDNS.
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 22 22:18:44 dv7 dhclient: Internet Systems Consortium DHCP Client 4.1-ESV-R4
Aug 22 22:18:44 dv7 dhclient: Copyright 2004-2011 Internet Systems Consortium.
Aug 22 22:18:44 dv7 dhclient: All rights reserved.
Aug 22 22:18:44 dv7 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 22 22:18:44 dv7 dhclient: 
Aug 22 22:18:44 dv7 NetworkManager[4519]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug 22 22:18:44 dv7 dhclient: Listening on LPF/wlan0/00:22:fa:d6:b4:ba
Aug 22 22:18:44 dv7 dhclient: Sending on   LPF/wlan0/00:22:fa:d6:b4:ba
Aug 22 22:18:44 dv7 dhclient: Sending on   Socket/fallback
Aug 22 22:18:44 dv7 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Aug 22 22:18:45 dv7 avahi-daemon[1263]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::222:faff:fed6:b4ba.
Aug 22 22:18:45 dv7 avahi-daemon[1263]: New relevant interface wlan0.IPv6 for mDNS.
Aug 22 22:18:45 dv7 avahi-daemon[1263]: Registering new address record for fe80::222:faff:fed6:b4ba on wlan0.*.
Aug 22 22:18:47 dv7 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 22 22:18:54 dv7 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Aug 22 22:18:54 dv7 kernel: [145855.896060] wlan0: no IPv6 routers present
Aug 22 22:19:04 dv7 NetworkManager[4519]: <info> (wlan0): IP6 addrconf timed out or failed.
Aug 22 22:19:04 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug 22 22:19:04 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug 22 22:19:04 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Aug 22 22:19:12 dv7 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Aug 22 22:19:23 dv7 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Aug 22 22:19:29 dv7 NetworkManager[4519]: <warn> (wlan0): DHCPv4 request timed out.
Aug 22 22:19:29 dv7 NetworkManager[4519]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 4933
Aug 22 22:19:29 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Aug 22 22:19:29 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Aug 22 22:19:29 dv7 NetworkManager[4519]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Aug 22 22:19:29 dv7 NetworkManager[4519]: <warn> Activation (wlan0) failed for access point (yildiz-net)
Aug 22 22:19:29 dv7 NetworkManager[4519]: <warn> Activation (wlan0) failed.
Aug 22 22:19:29 dv7 NetworkManager[4519]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Aug 22 22:19:29 dv7 NetworkManager[4519]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 22 22:19:29 dv7 NetworkManager[4519]: <info> (wlan0): deactivating device (reason 'none') [0]
Aug 22 22:19:29 dv7 avahi-daemon[1263]: Withdrawing address record for fe80::222:faff:fed6:b4ba on wlan0.
Aug 22 22:19:29 dv7 avahi-daemon[1263]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::222:faff:fed6:b4ba.
Aug 22 22:19:29 dv7 avahi-daemon[1263]: Interface wlan0.IPv6 no longer relevant for mDNS.
Aug 22 22:19:29 dv7 NetworkManager[4519]: <info> Policy set 'Wired connection 2' (easytether0) as default for IPv4 routing and DNS.
Aug 22 22:19:29 dv7 NetworkManager[4519]: <info> Policy set 'Wired connection 2' (easytether0) as default for IPv4 routing and DNS.
Aug 22 22:19:29 dv7 kernel: [145891.211711] wlan0: deauthenticating from 00:25:46:83:90:80 by local choice (reason=3)
Aug 22 22:19:30 dv7 wpa_supplicant[4528]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Aug 22 22:19:30 dv7 NetworkManager[4519]: <info> (wlan0): supplicant interface state: completed -> disconnected


```

### what I tried so far? ###

### 1. IPv6 was set to 'Ignore' (nm-applet settings -> wireless -> pick the network -> Edit -> IPv6 Settings -> Method: Ignore)
### Result: No change

### 2. A blog post suggested killing wpasupplicant process (URL not remembered)
### Result: wpasupplicant keeps coming back

### 3. A blog post suggested that aggressive power management might be the problem, and I turned off power management (sudo iwconfig wlan0 power off)
### Result: No change

### 4. Modified some kernel module options (sudo modprobe iwlwifi 11n_disable=1 swcrypto=1) and restrarted network
### Result: No change

### 5. I uninstalled nm-applet and network-manager, then installed wicd. 
### Result: Wicd cannot connect the university network as well (i.e. can associate but cannot connect)

### 6. I tried wpa_gui as well with no success

### 7. I tried other distributions (Fedora and LinuxMint) via LiveUSB and they exhibited similar behavor (associate but can not connect). This suggests that the problem is not because of Ubuntu per se. Maybe a kernel or gnome (NetworkManager) issue or wpasuplicant/dhclient issue.
  
### 8. A miracle lasted for one day only: At work i use LAN, since I cannot use wireless. One day, I was not able browse the net although the ethernet cable was connected. I thought the university router was down. So I decided to use cell phone's 3G network connection. I have an Android phone and it allows LAN-over-USB. I connected the USB cable between computer and cell phone. I started the EasyEther app. Then, the situation was similar, I am connected but I cannot browse the net (sorry I don't remember the error code Chrome provided). Then my friend suggested wireless connection via her iPhone. She activated the wireless network at her phone, I connected iPhone's network. And everything is same, I am connected but I cannot browse. So, I gave up. In the sequence given, I did; disconnect from iPhone's wireless network, turn off USB connection and pull the ethernet cable. Then I saw a miracle happened, nm-aplet notified that it is connected to university wireless network. And I was able to browse the net. It was a miracle. When it was about to leave work, I closed the lid (suspend). Unofortunately, next day, when I open the lid, I was not able to connect to university wireless network. Now I'm sure I can connect but I don't know how.

UPDATE1(09/27/2012): I tried Ubuntu 10.04.4 live USB and wireless worked without a problem. Then, in my 12.04 ubuntu installation, I tried to downgrade dhclient, wpasupplicant and network-manager packages to same versions that of ubuntu 10.04.4 but I couldn't deal with dependencies after a certain point.

UPDATE2(09/27/2012): One of HostAP maillist members suggested using different dhclients, and I tried udhcpc and dhcpcd with wicd. I didn't observe any changes and I'm not sure if dhcp clients weren't run properly or they ran but failed to obtain ip address.

---

### Post by einonm on 2012-09-21
Do you always suspend you laptop when not in use, or do you also power down completely? The suspend/resume cycle for some wifi drivers is known to cause issues.

---

### Post by alperyilmaz on 2012-09-23
Hi einonm,

I do both. Sometimes I just suspend. And sometimes I power it down.

---

### Post by einonm on 2012-09-23
As you've experienced this issue with several distros, it sounds like a kernel issue. I think you should try asking on the Linux Wireless IRC channel, and then perhaps the Linux wireless mailing list. The details are here:

[http://linuxwireless.org/en/users/Support](http://linuxwireless.org/en/users/Support)

---

### Post by alperyilmaz on 2012-09-27
I asked help at #linuxwireless IRC chat and then at linux-wireless maillist. They referred me to another maillist "hostAP".. Somebody gave suggestions from that maillist..

By the way, I tried Ubuntu 10.04.4 LTS with live USB and I can connect to my university wireless without a problem. So, it is working with older version of Ubuntu.

I tried to downgrade dhclient and wpasupplicant packages in my 12.04 installation but I couldn't deal with dependencies after a certain point.

---

### Post by tty0 on 2012-11-25
If you are still having this problem, continue to read :)

I assume, you are using iwlwifi (current intel drivers in 12.04) according to your logs.

1.) Use netwokmanager(nm-applet) to connect.
2.) Use this command before connect:

sudo rmmod iwlwifi && sudo modprobe iwlwifi swcrypto=1

Now you should be able to connect, I use this way to connect yildiz-net in 12.04.

---

