---
title: "wireless adapter detected twice???"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by lordpeterk on 2009-03-17
Hello, all.
I have just installed Ubuntu 8.10 and I am having trouble getting my D-Link DWL-G510 card to connect to my wireless network. I think part of the problem may be that the system has assigned two different logical names -- wifi0 and ath0 -- to this device, and it can't seem to make up its mind which one to allocate its resources to.

If I look at iwconfig it is ath0 all the way:

		iwconfig
	
	wifi0     no wireless extensions.
	
	ath0      IEEE 802.11g  ESSID:""  Nickname:""
	          Mode:Managed  Channel:0  Access Point: Not-Associated   
	          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
	          Retry: off   RTS thr: off   Fragment thr: off
	          Power Management: off
	          Link Quality=0/70  Signal level=-78 dBm  Noise level=-78 dBm
	          Rx invalid nwid:105902  Rx invalid crypt:0  Rx invalid frag:0
	          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

but then if I run lshw -c network it is just the other way around:

	sudo lshw -c network
	 
	  *-network               
	       description: Wireless interface
	       product: AR2413 802.11bg NIC
	       vendor: Atheros Communications Inc.
	       physical id: 11
	       bus info: pci@0000:00:11.0
	       logical name: wifi0
	       version: 01
	       serial: 00:15:e9:2c:35:88
	       width: 32 bits
	       clock: 33MHz
	       capabilities: pm bus_master cap_list logical ethernet physical wireless
	       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10
	module=ath_pci multicast=yes wireless=IEEE 802.11g

I am prettty sure it really ought to be one or the other but I don't know how to get rid of the duplication.

---

