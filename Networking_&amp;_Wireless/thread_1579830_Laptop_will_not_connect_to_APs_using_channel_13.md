---
title: "Laptop will not connect to APs using channel 13"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by notconnected0 on 2010-09-22
I'm relatively new to Ubuntu, and have just installed 10.04 on a toshiba portege M100 laptop.  Having got over the intel video chipset problems I tried to connect to my WLAN. 

Network manager would not connect.  I tried switching to WPA, WEP and no encryption.  No effect I still could not connect.  I also noticed that network manager can find other APs much more quickly than mine.

Haveing done some searching I tried removing network manager and installed wicd.  Was good at finding the AP but reported it as operatingon channel 0.  Still would not connect.  I tried changing the AP channel to 6, suddenly everyting worked.  I switched back to network manager (wicd got in a tangle over hidden networks).  Still works.

Having scoured the web for help I found reference to 10.04 kernel suporting US channels.  and that I should create a file /etc/modprobe.d/cfg80211, containing "options cfg80211 ieee80211_regdom=EU".  I have tried this and it doesnt have any effect.  I have noted that there are numerous variants of this advised by different people.

Whilst at home I can operate my AP n a US channel, when I am on the move I cannot.  I would like to get this working if at all possible.

For info the wireless adaptor reported is:
            *-network:1
                    description: Wireless interface
                    product: PRO/Wireless 2200BG [Calexico2] Network Connection
                    vendor: Intel Corporation
                    physical id: a
                    bus info: pci@0000:01:0a.0
                    logical name: eth1
                    version: 05
                    serial: 00:0e:35:93:be:61
                    width: 32 bits
                    clock: 33MHz
                    capabilities: pm bus_master cap_list ethernet physical wireless
                    configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.71 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11b
    [FONT=&quot]                resources: irq:11 memory:cfffe000-cfffefff[/FONT]

---

### Post by SteveDee on 2010-09-22
In a terminal type:-
iwlist channel

This should show the channels supported, and the current channel.

---

### Post by notconnected0 on 2010-09-23
Thanks

iwlist channel; Confirms that only channels 1-11 are configured.

Any clue as to how I can fix that?

---

### Post by psusi on 2010-09-23
I think it's the hardware.  If it was originally sold ( or supposed to be ) in the US, then it will only use the US channels.

---

### Post by notconnected0 on 2010-09-23
Okay, in trying to prove it its not the hardware I have made a little more progress.

[http://www.linuxquestions.org/questions/ubuntu-63/solved-intel-wifi-not-working-after-ubuntu-8-10-upgrade-689834/](http://www.linuxquestions.org/questions/ubuntu-63/solved-intel-wifi-not-working-after-ubuntu-8-10-upgrade-689834/)

talks about the identical problem on the same laptop (mine was originally sold in the UK).  However as far as I can see this fix (as above) only worked when there was a seperate driver for the Intel wireless card.  I understand this is now integrated into the kernel (not sure when from).

I tried a USB wireless dongle and that works okay.

I tried the 8.10 Live CD and the problem exists in that.

Above makes me thing this is a driver issue, but if the driver is in the kernel what if anything can I do!

Thanks

---

### Post by SteveDee on 2010-09-23
I don't think its your hardware. These wireless components have to support the international market, and regulations vary globally. Windows drivers normally have a regional setting, which is often all that is needed to get a "US" laptop to run channel 13.

I'm using the ipw2100 and run channel 13, and by typing: lspci -vv 
...in a terminal, I get:-

```

01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
	Subsystem: Intel Corporation Device 2561
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 8500ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 7
	Region 0: Memory at fcfff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Kernel driver in use: ipw2100
	Kernel modules: ipw2100

```

The output from iwlist shows your current config limitations, but I wonder if the Linux kernel simply limits the available channels based upon a Locale or Regional setting?

---

### Post by notconnected0 on 2010-09-25
I think I have found the cause, but not the solution.

It is in here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/57606](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/57606) which seems to have been abandoned as a bug. The IPW2200 driver uses the firmware region code to set the available  channels.  The windows driver does not, so units sold in Europe often  have the wrong firmware region set.  (Mine has "Custom ZZM" not "Europe ZZE"  or "US/Canada ZZA".  It would be nice to have the driver use the real locale rather than a random value!

The options cfg80211 ieee80211_regdom=EU fix doesnt affect the IPW2200 driver, and in ant case only applies to Ubuntu 8.10.

There seems to be a lot of hacks to correct the region code in the firmware (e.g. [http://saftware.de/#ipw2200](http://saftware.de/#ipw2200)), but I think those may be beyond me to do .  If anyone can point me at a ready "Patched" ipw2200 I would be very grateful.

---

### Post by scrooge_74 on 2010-09-25
Is not the best, but better get a usb wifi dongle

---

