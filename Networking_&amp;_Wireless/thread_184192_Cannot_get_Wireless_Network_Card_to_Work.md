---
title: "Cannot get Wireless Network Card to Work"
date: 2006-05-29
forum: Networking &amp; Wireless
---

### Post by shepto on 2006-05-29
I am trying to configure wireless card on my laptop, without success.

The card is a Linksys WPC54G v1.2.
The laptop is an IBM Thinkpad 600E.
The platform is Ubuntu 5.10

I have followed the steps as per configuration instructions posted elsewhere on this site. I have:
	1/ installed and compiled ndiswrapper 1.1
	2/ Looked up my card in the list of supported cards and downloaded the recommended drivers
	3/ Copied the driver and inf file to the laptop
	4/ sudo ndiswrapper -i lsbcmnds.inf
	5/ sudo modprobe ndiswrapper
	6/ sudo ifup wlan0

This all went fine. The only time the installed strayed from what was documented was in step 4. Here some documentation suggests I should see some output along the lines of "Forcing RadioState:0 to RadioState:1" after which I would have to edit the generated config files, changing all occurrences of "RadioState:1" back to "RadioState:0". The only output I get is "installing lsbcmnds" and when I check my config files, I only see "RadioState:0" and never "RadioState:1" so I don't see this an an issue.

The problem is that "sudo iwlist wlan0 scan" shows "wlan0 No scan results" whatever I try so my card will not connect to the router. 

The laptop appears to be recognising the card correctly. I have listed some commands and their output below:

sudo ndiswrapper -l
	Installed ndis drivers:
	lsbcmnds	driver present, hardware present 

sudo lshw -C network
	network
		description: network controller
		product: BCM406 802.11b/g Wirless LAN Controller
		vendor: Broadcom Corporation
		physical id: 1
		bus info: pci@06:00.0
		logical name: wlan0
		version: 03
		serial: 00:12:17:b6:7f:bb
		width: 32 bits
		clock: 33 MHz
		capabilities: bus_master cap_list ethernet physical wireless
		configuration: broadcast=yes driver=ndiswrapper link=no multicast=yes wireless=IEEE 802.11g
		resources: iomemory:8c00000-8c01fff

sudo lspci -v
	0000:06:00.0 Network conroller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN 		Controller (rev 03)
		Subsystem: Linksys WPC54G
		Flags: bus master, fast devsel, latency 64, IRQ 9
		Memory at 08c00000 (32-bit, non-prefetchable) [size=8k]
		Capabilities: [40] Power Management version 2

sudo dmesg
	ndiswrapper: using irq 9
	wlan0: ndiswrapper ethernet device 00:12:17:b6:7f:bb using driver lsbcmnds, configuration file 4E4:4320.5.conf
	wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP

sudo iwconfig
	lo	no wireless extensions
	sit0	no wireless extensions
	wlan0	IEEE 802.11g ESSID:off/any
		Mode: Managed	Frequency:2.437 GHz	Access Point: 00:00:00:00:00
		Bit rate: 54 Mb/s	Tx-Power:14 dBm
		RTS thr: 2347 B	Fragment thr: 2436 B
		Encryption key: off
		Power Management: off
		Link Quality:100/100	signal level: -10 dBm	Noise level: -256 dBm
		Rx invalid nwid:0	Rx invalid crypt:0	Rx invalid frag:0
		Tx excessive retries:0 Invalid misc:33 missed beacon:0


The router is working correctly as I am already connecting to it wirelessly via another PC. I haven't been able to confirm if the card is working correctly on another laptop but the card was bought new so should be OK. I have tried removing and re-compiling ndiswrapper, different drivers (bcmwl5/bcmwl5a) and pressing all combinations of FN-F(x) in case the wireless network component is disabled on the laptop (the output suggests it is isn't).

I'm now out of ideas. Has anyone out there got any pointers?

---

### Post by WakkiTabakki on 2006-05-29
After you've got the network card up and running via ndiswrapper, use the NetworkManager application. This app has it's own configuration, so no mucking about with /etc/network/interfaces and stuff...

Check it out!
[http://ubuntuforums.org/showthread.php?t=125150&highlight=networkmanager+howto]("http://ubuntuforums.org/showthread.php?t=125150&highlight=networkmanager+howto")
[http://ubuntuforums.org/showthread.php?t=176979&highlight=networkmanager+howto]("http://ubuntuforums.org/showthread.php?t=176979&highlight=networkmanager+howto")


Good luck
/N

---

### Post by skyshark88 on 2006-05-29
Try the configure network card module from the add/remove program, it congigured my usb network dongle when all else failed.......

---

### Post by shepto on 2006-05-31
Thanks for the ideas.

I tried to use the "Configure Network Card" via the "Add Applications" menu option but it didn't work. The error messages were numerous and varied but all related to the fact that my laptop couldn't retrieve various files from various network addresses. Mention was made that the install would try and retrieve the missing files from my local repository if available, otherwise the install would fail. I presume the latter was the case as the "Configure Netword Card" option remained disabled after the install had completed. Unfortunately I do not have an ethernet card to enable me to connect my laptop to the network.

Regarding the use of the Network Manager, I see from the posts that it is only supported on Dapper, although someone has got it going on their Breezy install by updating the kernel. As this is the first thing I've tried on this laptop, I might as well install Dapper and start again. I'll give this a go - unless anyone has anything less drastic they can suggest to save my Breezy install from being wiped?

---

### Post by nickm on 2006-05-31
you could try what i did if your going to go the dapper route: 
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

It worked for my linksys card where Ndis didnt.

---

