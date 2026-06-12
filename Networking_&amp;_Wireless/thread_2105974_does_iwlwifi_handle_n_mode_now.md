---
title: "does iwlwifi handle n mode now ?"
date: 2013-01-17
forum: Networking &amp; Wireless
---

### Post by ft_ on 2013-01-17
hi,

it was not the case until recently, so does the iwlwifi driver work now flawlessly with wifi n access points ?

Thanks !

---

### Post by ft_ on 2013-01-18
[http://lkml.indiana.edu/hypermail/linux/kernel/1301.2/01599.html](http://lkml.indiana.edu/hypermail/linux/kernel/1301.2/01599.html)

seems to contain some improvements about iwlwifi.

---

### Post by 67GTA on 2013-01-25
I was using wireless N with 12.10 and iwlwifi. I have a Centrino Wireless-N 2230 card. What does ```
sudo lshw -C net
``` say?

---

### Post by ft_ on 2013-01-25
```
produit: Centrino Advanced-N 6205 [Taylor Peak]
       fabriquant: Intel Corporation
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       nom logique: wlan2
       version: 34
       numéro de série: xxx
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-1-generic firmware=18.168.6.1 ip=192.168.1.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       ressources: irq:47 mémoire:f1400000-f1401fff

```

I can connect in N mode, but I get many errors in iwconfig, and the connection speed often slow down to 1 Mb/s. Avoiding N mode in my wireless router makes my connection by far better (even with a max speed slightly inferior) especially when the signal is weak.

---

### Post by 67GTA on 2013-01-25
I ran across this [http://askubuntu.com/questions/190262/wifi-slow-sometimes-reboot-helps-how-do-i-debug-it](http://askubuntu.com/questions/190262/wifi-slow-sometimes-reboot-helps-how-do-i-debug-it)

It seems to be a random iwlwifi bug. Maybe it will help?
[]("http://askubuntu.com/questions/190262/wifi-slow-sometimes-reboot-helps-how-do-i-debug-it")

---

### Post by ju2wheels on 2013-01-25
```

$ sudo lspci -vv

.....

03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 55
	Region 0: Memory at f3900000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
		Address: 00000000fee003b8  Data: 0000
	Capabilities: [e0] Express (v1) Endpoint, MSI 00
		DevCap:	MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 unlimited
			ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset+
		DevCtl:	Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
			RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+ FLReset-
			MaxPayload 128 bytes, MaxReadReq 128 bytes
		DevSta:	CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr+ TransPend-
		LnkCap:	Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <4us, L1 <32us
			ClockPM+ Surprise- LLActRep- BwNot-
		LnkCtl:	ASPM L1 Enabled; RCB 64 bytes Disabled- Retrain- CommClk+
			ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
		LnkSta:	Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
	Capabilities: [100 v1] Advanced Error Reporting
		UESta:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UEMsk:	DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
		UESvrt:	DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
		CESta:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		CEMsk:	RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
		AERCap:	First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
	Capabilities: [140 v1] Device Serial Number 10-0b-a9-ff-ff-8d-d9-b8
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi


.....

```

I have the same model on my thinkpad and I get great wireless-N speed (between 8-10MB/s internally pc to pc, both wireless n, 3-5Mb/s from internet). Heres a peak transfer graph from my router for today (I was rsyncing centos so I couldnt hit peak today internally on my network):

[IMG]http://i.imgur.com/MsCoTGy.png[/IMG]

I dont know if this is fast compared to other people's setup but its the fastest ive ever achieved on my setup (dual band n router). The only way I can get these speeds is by custom tweaking the options for the wifi modules on all my Linux pc's, otherwise its not achievable from my testing.

Here is basically what I do:

```

$ modinfo iwlwifi
filename:       /lib/modules/3.2.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
alias:          iwlagn
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
.... [removed]
srcversion:     C9C876E115EE7BFFAFB2FA7
alias:          pci:v00008086d00000892sv*sd00000466bc*sc*i*
.... [removed]
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-36-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           ack_check:Check ack health (default: 0 [disabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (default: true) (bool)

```

Ok so the most important part is the depends (other modules this module uses which may have more options) and the parameters (parm) each module supports.

Using these parameters I create a file (/etc/modprobe.d/iwlwifi.conf) for modprobe and specify values for the options I want to modify for each module as follows:

```

options cfg80211 cfg80211_disable_40mhz_24ghz=0
options iwlwifi fw_restart=1 bt_ch_inhibition=1 bt_coex_active=1 swcrypto=1

```

Note that even though some of the options I set are listed as default in the module, I still set them explicitly to make sure. So router config/signal issues aside, tweaking your settings like this helps a hell of a lot. Be sure to reboot for those settings to take effect.

Hope that helps.

---

### Post by Bucky Ball on 2013-01-25
Does this actually refer to a testing 13.04 install? You don't mention. If not, I will move to the appropriate sub-forum.

---

### Post by screaminj3sus on 2013-01-25
its always handled N mode fine for me, never had any problems.

---

### Post by ft_ on 2013-01-26
I noticied that the two numbers in bold are quite big with N mode and rather low with BG mode :

```
wlan2     IEEE 802.11abgn  ESSID:"my-AP"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <mac>  
          Bit Rate=5.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:**HERE**  Invalid misc:**HERE**   Missed beacon:0
```

---

### Post by ronacc on 2013-01-26
@ ju2wheels What are you using to get that neat networking display ?

---

### Post by ju2wheels on 2013-01-27
@ronacc: The graph is part of my router's firmware, i think its based on dd-wrt

---

### Post by ju2wheels on 2013-01-27
> **ft_ said:**
> I noticied that the two numbers in bold are quite big with N mode and rather low with BG mode :

```
wlan2     IEEE 802.11abgn  ESSID:"my-AP"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <mac>  
          Bit Rate=5.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:**HERE**  Invalid misc:**HERE**   Missed beacon:0
```

I would worry more about the link quality/bit rate shown than the excessive retires/invalid misc. I have high values for excessive retries/invalid misc but still get great speeds, but its all dependent on the link quality/bit rate. Some things to check are whether your router is set for 20/40mhz bandwith and tweaking the Tx Power so you get the best possible link quality (I test my router in increments of 10mW from 60mW-120mW to find the tx power that gave me the best and most stable link quality/bit rate).

```

wlan0     IEEE 802.11abgn  ESSID:"my_wifi"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: <hex>   
          Bit Rate=240 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2436127  Invalid misc:383   Missed beacon:0


```

---

### Post by ft_ on 2013-01-27
Ok for the bold numbers.
I can't change anything on my router.
The signal is weak in some places of my house, ok. But BG mode works flawlessly while N mode often shows a 1Mb/s rate. Is it possible that N mode is not recommended with weak signals ?

---

### Post by forcecore on 2013-01-27
I remember that problem 3 years ago with my 4965AGN, currently i do not know because my router is older BG, but i still cannot belive this problem still exists? lets hope fix arrives because i have too Intel Ultimate 6300 and some other older Intel N card. I planned to buy N router but now....maybe not if it is useless. ft_ and everyone with this problem do not loose hope.

---

### Post by Bucky Ball on 2013-01-27
As there has been no response to my first post:

*Thread moved to **Networking & Wireless***

---

### Post by ahallubuntu on 2013-01-27
I've been using 802.11n and iwlwifi since 10.04 LTS.  I use the Intel 5100 card in several laptops.  I recently moved to 12.04 LTS and the transfer rate seems about the same.

But there may have been some improvements in the iwlwifi driver.  For example, in 10.04, after resume from suspend, it would sometimes take a few seconds before the wireless card would try to re-connect to my network; sometimes I even disabled the card and re-enabled it to make it happen more quickly.  In 12.04, this is unnecessary - wireless connection starts very quickly after resume.  I don't know if this is due to the iwlwifi driver or other improvements in Ubuntu.

I am not close to my router but I still get solid connections and sustained LAN transfer of about 5MBytes/sec when transferring files.

---

### Post by forcecore on 2013-01-27
ahallubuntu: have you tested 13.04 lastest what is your results? it woult be very informative for future preparations.

---

### Post by ahallubuntu on 2013-01-27
I haven't tested 13.04.  I won't be installing it myself unless I have to - I prefer the LTS versions, and 12.04 is working great for me.  I'll probably try out 13.04 after it is released.  I understand that Ubuntu is moving to "rolling releases" soon between LTS versions anyway as Mint does now.

But if I have some spare time I'll try one of the pre-release versions of 13.04.

---

