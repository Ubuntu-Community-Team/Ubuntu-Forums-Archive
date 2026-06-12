---
title: "Struggeling with wireless...."
date: 2006-05-19
forum: Networking &amp; Wireless
---

### Post by SSamiK on 2006-05-19
I have installed the Ubuntu base system on a old Packard Bell "Easy One Dc"  and one problem I can't seem to get my head around is the wireless network.. I've tried every "howto" i could find, read many posts in the forum and searched around but no luck in sorting it out...yet. There is no other ethernet interface on the machine to help in the proccess of getting the wireless up and running. 

The Problem:   I seem to be getting an IP from the router, but still I can't browse the web. My wifi card is a "Phillips Wireless Notebook Adapter
SNN6500/00" with a atheros AR5212 chipset.
I get a "Destination Host Unreachable" when pinging an ip, and "unknown host" when pinging an adress as google.com.

Here is my outputs from different commands;

lspci:	0000:06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)



ifconfig:


ath0
	Link encap:Ethernet HWaddr 00:30:F1:BF:62:2F
	inet addr:192.168.0.118 Bcast:192.168.0.255 Mask:255.255.255.0
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:11 errors:0 dropped:0 overruns:0 frame:0
	TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:200
	RX bytes:1442 (1.4 KiB) TX bytes:2322 (2.2 KiB)
	Interrupt:10 Memory:c4b60000.c4b70000

lo	
Link encap:Local Loopback
	inet addr:127.0.0.1 Mask:255.0.0.0
	UP LOOPBACK RUNNING MTU:16436 Metric:1
	RX packets:13 errors:0 dropped:0 overruns:0 frame:0
	TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:1189 (1.1 KiB) TX bytes:1189 (1.1 KiB)


iwconfig:

lo	
no wireless extensions

ath0
IEEE 802.11g ESSID:"myssid"
	Mode:Managed Frequency:2.412 Ghz Access Point: 00:0D:88:07:6B:26
	Bit Rate:11Mb/s Tx-Power:18dBm Sensitivity=0/3
	Retry:off RTS thr:off Fragment thr:off
	Power Mangament:off
	Link Quality=47/94 Signal level=-48 dBm Noise level=-95 dBm
	Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
	Tx excessive retries:0 Invalid misc:0 Missed beacon:0


ROUTE:
route -n
192.168.0.0,	0.0.0.0,		255.255.255.0,	U,	0,	0,	0,	ath0,
0.0.0.0,		192.168.0.1,	0.0.0.0,		UG,	0,	0,	0,	ath0,	

IWLIST:
sudo iwlist ath0 scan

ath0
Scan completed :
	Cell 01 Address: 00:0D:88:07:6B:26
	ESSID:"myssid"
	Mode:Master
	Frequency:2.412 GHz (Channel 1)
	Quality=47/94 Signal level=-48 dBm Noise level=-95 dBm
	Encryption key:off
	Bit Rates:1 Mb/s; 2 Mb/s; 5Mb/s; 11Mb/s; 22Mb/s
	Extra:bcn_int=100



Can anyone see anything wrong, or knows what to do in this particular case?  If more info is needed, i'll post it. I really really need to get this working.

---

### Post by spd106 on 2006-05-20
Just to clarify, can you ping the router?

If so, then it could be a dns issue. Check the /etc/resolv.conf file for nameservers. Then log in to the router and go over it's configuration. You should be provided with DNS server addresses by your ISP, though not always automatically.

If not then i'm not sure what to do. It could be the card that's misconfigured. Maybe try ejecting it and plugging back in again. Have you been able to get the latest updates? You can always download the .deb files and then transfer them over to the PC via usb stick or whatever.

Good luck

---

### Post by SSamiK on 2006-05-21
When trying to ping the router i only get a  "Destination Host Unreachable" error. /etc/resolv.conf got two DNS server adresses in it, so it seems to be ok. 
In my router erveything also seems to be all set to go, and it should be...5 other computers (both Windows and Ubuntu) connected trought it works like a charm. In the DHCP server page I can see the MAC Address from the non connective box, with an IP. (my router is a D-link DI-714P+) 
No luck in getting updates, and always running into dependencies problems when trying to move .deb's with a USB stick.  :-( 

I also got a 3COM OfficeConnect Wireless 54Mbps 11g Compact USB Adapter and a D-link G650+ PCMCIA card maby one of those is a bit more easy to get working.



[SOLVED] Problem solved by changing to the D-link G650+ card, downloading 
[http://195.66.192.167/linux/acx_patches/fw/acx111_1.2.1.34/tiacx111c16](http://195.66.192.167/linux/acx_patches/fw/acx111_1.2.1.34/tiacx111c16) and updating firmware in /lib/firmware/2.6.15-18-386/acx/2.3.1.31   ( as described in [http://ubuntuforums.org/showthread.php?t=145836&highlight=acx]("http://ubuntuforums.org/showthread.php?t=145836&highlight=acx") Post #3 )

After a reboot everything works just fine.

---

