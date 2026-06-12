---
title: "slow ethernet &amp; wlan, really confusin (linux mint)"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by Il_Literacy on 2010-11-28
okay, this has bugged me for weeks now. I posted this before to mint forums but I post here, in case someone here would have a fix.

My problem is, that in my dorm room, internet is slow, or not slow, but it sometimes goes the speed it should (between 60 - 100 megas/s) but then, suddenly it slows down under to 1 mega/s. Most of the time, it is under 1. This problem is only on my computer, and only in my dorm room. IT person has tried reseting the router here but it wont work, but this problem appears nowhere else. Not back in my home, not at my uncles/aunts place.

here is info on my connection:

os: linux mint 9

hardware info:

Ethernet controller	Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
Network controller	Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

03:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  03)
	Subsystem: ASUSTeK Computer Inc. Device [1043:16d5]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 28
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at f9fff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at f9ff8000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at feaf0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:00.0  Network controller [0280]: Atheros Communications Inc. AR9285 Wireless  Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Device [1a3b:1089]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

and info on the realtek one with rtl8139diag

rtl8139-diag.c:v2.13 2/28/2005 Donald Becker ([EMAIL="becker@scyld.com"]becker@scyld.com[/EMAIL])
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
Index #1: Found a RealTek (unknown chip type) adapter at 0xe800.
Realtek station address 48:5b:39:81:bc:8f, chip type 'Unknown version'.
  Receiver configuration: Normal unicast and hashed multicast
     Rx FIFO threshold 1024 bytes, maximum burst 1024 bytes, 8KB ring
  Transmitter enabled with NONSTANDARD! settings, maximum burst 1024 bytes.
  Flow control: Tx disabled  Rx disabled.
  The chip configuration is 0x04 0x0f, MII half-duplex mode.
  No interrupt sources are pending.
 Use '-a' or '-aa' to show device registers,
     '-e' to show EEPROM contents, -ee for parsed contents,
  or '-m' or '-mm' to show MII management registers.

extended info

rtl8139-diag.c:v2.13 2/28/2005 Donald Becker ([EMAIL="becker@scyld.com"]becker@scyld.com[/EMAIL])
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
Index #1: Found a RealTek (unknown chip type) adapter at 0xe800.
The RealTek chip appears to be active, so some registers will not be read.
To see all register values use the '-f' flag.
RealTek chip registers at 0xe800
 0x000: 81395b48 00008fbc 00000040 00801080 00000000 00000000 000090ca fd50fd50
 0x020: 343c0000 00000000 2078ce00 2058de02 00000000 0c000000 00000000 0000803f
 0x040: 2b3006c0 0000c60e 42520618 425206a0 bc0f0401 01000462 00000000 c0350000
 0x060: 80001000 27ffff01 0000f70c f080018b a15afcc2 00000000 00000000 00950000.
Realtek station address 48:5b:39:81:bc:8f, chip type 'Unknown version'.
  Receiver configuration: Normal unicast and hashed multicast
     Rx FIFO threshold 1024 bytes, maximum burst 1024 bytes, 8KB ring
  Transmitter enabled with NONSTANDARD! settings, maximum burst 1024 bytes.
    Tx entry #0 status 00000000 incomplete, 0 bytes.
    Tx entry #1 status 00000000 incomplete, 0 bytes.
    Tx entry #2 status 000090ca complete, 202 bytes.
    Tx entry #3 status 23102310 incomplete, 784 bytes.
   Tx out-of-window collision
  Flow control: Tx disabled  Rx disabled.
  The chip configuration is 0x04 0x0f, MII half-duplex mode.
  No interrupt sources are pending.
Decoded EEPROM contents:
   PCI IDs -- Vendor 0000, Device 0000.
   PCI Subsystem IDs -- Vendor 0000, Device 0000.
   PCI timer settings -- minimum grant 0, maximum latency 0.
  General purpose pins --  direction 0x00  value 0x00.
  Station Address 00:00:00:00:00:00.
  Configuration register 0/1 -- 0x00 / 0x00.
 EEPROM active region checksum is 0000.
 The RTL8139 does not use a MII transceiver.
 It does have internal MII-compatible registers:
   Basic mode control register   0x8000.
   Basic mode status register    0xff01.
   Autonegotiation Advertisement 0x27ff.
   Link Partner Ability register 0xf70c.
   Autonegotiation expansion     0x0000.
   Disconnects                   0x018b.
   False carrier sense counter   0xf080.
   NWay test register            0xfcc2.
   Receive frame error count     0xa15a.

- - - - - -

ethtool info:

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

- - - - - - 

info on host & dig for whatsmyip.com & cat /etc/resolv.conf

host:

anttoni@anttoni-laptop ~ $ host [www.whatismyip.com]("http://www.whatismyip.com/")

;; connection timed out; no servers could be reached

anttoni@anttoni-laptop ~ $ host [www.whatismyip.com]("http://www.whatismyip.com/")

[www.whatismyip.com]("http://www.whatismyip.com/") has address 72.233.89.199
[www.whatismyip.com]("http://www.whatismyip.com/") has address 72.233.89.198
[www.whatismyip.com]("http://www.whatismyip.com/") has address 72.233.89.197
[www.whatismyip.com]("http://www.whatismyip.com/") has address 72.233.89.200

anttoni@anttoni-laptop ~ $ host [www.whatismyip.com]("http://www.whatismyip.com/")

;; connection timed out; no servers could be reached

dig:

anttoni@anttoni-laptop ~ $ dig [www.whatismyip.com]("http://www.whatismyip.com/")

; <<>> DiG 9.7.0-P1 <<>> [www.whatismyip.com]("http://www.whatismyip.com/")
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31841
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;[www.whatismyip.com]("http://www.whatismyip.com/").            IN      A

;; ANSWER SECTION:
[www.whatismyip.com]("http://www.whatismyip.com/").     547     IN      A       72.233.89.199
[www.whatismyip.com]("http://www.whatismyip.com/").     547     IN      A       72.233.89.198
[www.whatismyip.com]("http://www.whatismyip.com/").     547     IN      A       72.233.89.197
[www.whatismyip.com]("http://www.whatismyip.com/").     547     IN      A       72.233.89.200

;; Query time: 9 msec
;; SERVER: 10.98.14.215#53(10.98.14.215)
;; WHEN: Mon Nov  8 14:33:15 2010
;; MSG SIZE  rcvd: 100

cat resolv:

anttoni@anttoni-laptop ~ $ cat /etc/resolv.conf
# Generated by NetworkManager
domain humak.local
search humak.local
nameserver 10.98.14.215
nameserver 10.98.14.217

- - - - - - -

nslookup for humak.fi and alkio.fi

anttoni@anttoni-laptop ~ $ nslookup [www.humak.fi]("http://www.humak.fi/")
;; connection timed out; no servers could be reached

anttoni@anttoni-laptop ~ $ nslookup [www.humak.fi]("http://www.humak.fi/")
Server:         10.98.14.215
Address:        10.98.14.215#53

[www.humak.fi]("http://www.humak.fi/")    canonical name = [ridnitsohkka.humak.edu]("http://ridnitsohkka.humak.edu/").
Name:   [ridnitsohkka.humak.edu]("http://ridnitsohkka.humak.edu/")
Address: 10.98.14.26

anttoni@anttoni-laptop ~ $ nslookup [www.alkio.fi]("http://www.alkio.fi/")
Server:         10.98.14.215
Address:        10.98.14.215#53

Non-authoritative answer:
[www.alkio.fi]("http://www.alkio.fi/")    canonical name = [bitter.artio.net]("http://bitter.artio.net/").
Name:   [bitter.artio.net]("http://bitter.artio.net/")
Address: 195.191.122.6

- - - - - - -

here is all the information on the situation. As stated before, this happens ONLY at my dorm room and ONLY to me. It affects firefox, IRC and MSN Messenger (phone bill shot through the roof because this, I have to keep contact to my girlfriend somehow. . .)

if anyone has _ANY_ idea what this is about, I would appreciate it. . .

---

### Post by uncaspi on 2010-11-28
Connect and shut down all running applications and open a terminal and type

sudo tcpdump -i eth0

and see if there is traffic through your card. For eth0 put in the right logical name for the card connected.

If there is heavy traffic you probably been visited by intruders.

---

### Post by Il_Literacy on 2010-11-28
I don't know if this is normal, but here is some of my tcpdump:

[SIZE=1]anttoni@anttoni-laptop ~ $ sudo tcpdump -i eth0
[sudo] password for anttoni: 
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
22:38:49.017853 ARP, Request who-has 10.98.6.88 tell 10.98.6.60, length 46
22:38:49.018688 IP anttoni-laptop.local.36564 > 10.98.14.215.domain: 140+ PTR? 88.6.98.10.in-addr.arpa. (41)
22:38:49.078885 IP 10.98.6.17.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:38:49.846281 IPX c78a8cc5.00:80:91:51:32:73.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_05321331[|ipx 64]
22:38:50.162041 ARP, Request who-has 10.98.6.88 tell 10.98.6.60, length 46
22:38:50.264978 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:38:50.293101 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:38:50.321487 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:38:50.461804 IPX c78a8cc5.00:80:91:6b:56:76.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_07034486[|ipx 64]
22:38:51.829375 IP 10.98.6.17.netbios-dgm > 10.98.6.255.netbios-dgm: NBT UDP PACKET(138)
22:38:51.829404 IP 10.98.6.17.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:38:52.039778 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:38:52.578843 IP 10.98.6.17.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:38:52.989363 (NOV-ETHII) IPX 07012000.00:21:5e:4e:ac:dc.0452 > 07012000.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp FileServer 'ALKIO[|ipx 448]
22:38:52.989381 IPX c78a8cc5.00:21:5e:4e:ac:dc.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp FileServer 'ALKIO[|ipx 448]
22:38:52.989389 (NOV-ETHII) IPX eef7dd94.00:21:5e:4e:ac:dc.0452 > eef7dd94.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp FileServer 'ALKIO[|ipx 448]
22:38:53.099194 (NOV-ETHII) IPX 07012000.00:21:5e:4e:ac:dc.0452 > 07012000.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp 0293 'ALKIO[|ipx 448]
22:38:53.099217 IPX c78a8cc5.00:21:5e:4e:ac:dc.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp 0293 'ALKIO[|ipx 320]
22:38:53.099225 (NOV-ETHII) IPX eef7dd94.00:21:5e:4e:ac:dc.0452 > eef7dd94.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp 0293 'ALKIO[|ipx 448]
22:38:53.328830 IP 10.98.6.17.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:38:54.020514 IP anttoni-laptop.local.57590 > ad2.humak.local.domain: 140+ PTR? 88.6.98.10.in-addr.arpa. (41)
22:38:54.278142 ARP, Request who-has 10.98.6.88 tell 10.98.6.60, length 46
22:38:54.929675 ARP, Request who-has 10.98.6.16 tell 10.98.6.17, length 46
22:38:55.039156 ARP, Request who-has 10.98.6.88 tell 10.98.6.60, length 46
22:38:55.381627 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:38:55.413183 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:38:55.445359 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:38:56.031324 ARP, Request who-has 10.98.6.88 tell 10.98.6.60, length 46
22:38:56.078836 IP 10.98.6.17.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:38:56.828810 IP 10.98.6.17.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:38:57.167815 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:38:57.578805 IP 10.98.6.17.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:38:59.025630 IP anttoni-laptop.local.36564 > 10.98.14.215.domain: 140+ PTR? 88.6.98.10.in-addr.arpa. (41)
22:39:00.484779 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:00.522401 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:00.551948 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:00.953755 ARP, Request who-has 10.98.6.16 tell 10.98.6.17, length 46
22:39:02.269585 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:39:04.030726 IP anttoni-laptop.local.57590 > ad2.humak.local.domain: 140+ PTR? 88.6.98.10.in-addr.arpa. (41)
22:39:05.369624 00:19:4b:ab:51:3f (oui Unknown) > Broadcast Null Supervisory, Receiver not Ready, rcv seq 64, Flags [Poll], length 46
22:39:05.381511 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:19:4b:ab:51:3f (oui Unknown), length 265
22:39:05.402511 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:19:4b:ab:51:3f (oui Unknown), length 273
22:39:05.585999 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:05.618129 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:05.648504 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:05.965234 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/2 (Cache flush) PTR[|domain]
22:39:05.966995 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/2[|domain]
22:39:06.215859 IP iPhone.local.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QU)? iPhone.local. ANY (QU)? iPhone.local. (80)
22:39:06.226678 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0 [2q] [2n][|domain]
22:39:06.466171 IP iPhone.local.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QM)? iPhone.local. ANY (QM)? iPhone.local. (80)
22:39:06.468172 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0 [2q] [2n][|domain]
22:39:06.716989 IP iPhone.local.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QM)? iPhone.local. ANY (QM)? iPhone.local. (80)
22:39:06.719507 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0 [2q] [2n][|domain]
22:39:06.954695 ARP, Request who-has 10.98.6.16 tell 10.98.6.17, length 46
22:39:06.965511 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/2 (Cache flush) PTR[|domain]
22:39:06.968953 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/2[|domain]
22:39:07.072294 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/1 (Cache flush) A 10.98.6.184, (88)
22:39:07.075837 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/1[|domain]
22:39:07.317599 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:39:08.066109 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/1 (Cache flush) A 10.98.6.184, (88)
22:39:08.067331 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/1[|domain]
22:39:08.967673 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/2 (Cache flush) PTR[|domain]
22:39:08.971906 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/2[|domain]
22:39:09.134632 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 88.6.98.10.in-addr.arpa. (41)
22:39:10.074383 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/1 (Cache flush) A 10.98.6.184, (88)
22:39:10.076215 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/1[|domain]
22:39:10.136757 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 88.6.98.10.in-addr.arpa. (41)
22:39:10.682266 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:10.711059 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:10.738770 IP6 fe80::225:b3ff:feec:d4fe.546 > ff02::1:2.547: dhcp6 solicit
22:39:10.751999 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:12.138200 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 88.6.98.10.in-addr.arpa. (41)
22:39:12.516610 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:39:12.956820 ARP, Request who-has 10.98.6.16 tell 10.98.6.17, length 46
22:39:12.969740 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 4/0/3 (Cache flush) PTR[|domain]
22:39:12.977215 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 4/0/3[|domain]
22:39:14.035715 IP anttoni-laptop.local.45675 > 10.98.14.215.domain: 54599+ PTR? 60.6.98.10.in-addr.arpa. (41)
22:39:15.806884 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:15.845556 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:15.874265 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:16.414130 ARP, Request who-has 10.98.6.1 tell 10.98.6.192, length 46
22:39:16.700735 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:39:17.489482 IP6 fe80::19c8:116c:7fad:f69c.546 > ff02::1:2.547: dhcp6 solicit
22:39:18.485910 IP6 fe80::19c8:116c:7fad:f69c.546 > ff02::1:2.547: dhcp6 solicit
22:39:18.959136 ARP, Request who-has NPI83BC9D.local tell 10.98.6.17, length 46
22:39:18.961961 ARP, Request who-has NPIECD4FE.local tell 10.98.6.17, length 46
22:39:19.032461 ARP, Request who-has 10.98.6.1 tell anttoni-laptop.local, length 28
22:39:19.032871 ARP, Reply 10.98.6.1 is-at 00:23:5e:37:47:40 (oui Unknown), length 46
22:39:19.040849 IP anttoni-laptop.local.48014 > ad2.humak.local.domain: 54599+ PTR? 60.6.98.10.in-addr.arpa. (41)
22:39:19.049899 IP ad2.humak.local.domain > anttoni-laptop.local.48014: 54599 NXDomain 0/1/0 (118)
22:39:19.150430 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 60.6.98.10.in-addr.arpa. (41)
22:39:19.166678 IP 10.98.6.90.netbios-dgm > 10.98.6.255.netbios-dgm: NBT UDP PACKET(138)
22:39:19.171860 ARP, Request who-has 10.98.6.90 tell anttoni-laptop.local, length 46
22:39:19.556542 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:39:19.803340 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:39:19.846705 IPX c78a8cc5.00:80:91:51:32:73.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_05321331[|ipx 64]
22:39:20.151808 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 60.6.98.10.in-addr.arpa. (41)
22:39:20.461210 IPX c78a8cc5.00:80:91:6b:56:76.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_07034486[|ipx 64]
22:39:20.488343 IP6 fe80::19c8:116c:7fad:f69c.546 > ff02::1:2.547: dhcp6 solicit
22:39:20.925896 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:20.952737 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:20.979307 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:22.153274 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 60.6.98.10.in-addr.arpa. (41)
22:39:22.704508 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:39:22.919373 (NOV-ETHII) IPX 07012000.00:21:5e:4e:ac:dc.0453 > 07012000.ff:ff:ff:ff:ff:ff.0453: ipx-rip-resp 19088743/1.2 4009221524/1.2 3347745989/1.2
22:39:22.919388 IPX c78a8cc5.00:21:5e:4e:ac:dc.0453 > c78a8cc5.ff:ff:ff:ff:ff:ff.0453: ipx-rip-resp 117514240/1.2 19088743/1.2 4009221524/1.2
22:39:22.919395 (NOV-ETHII) IPX eef7dd94.00:21:5e:4e:ac:dc.0453 > eef7dd94.ff:ff:ff:ff:ff:ff.0453: ipx-rip-resp 117514240/1.2 19088743/1.2 3347745989/1.2
22:39:24.052712 IP anttoni-laptop.local.51876 > 10.98.14.215.domain: 25680+ PTR? 215.14.98.10.in-addr.arpa. (43)
22:39:24.490937 IP6 fe80::19c8:116c:7fad:f69c.546 > ff02::1:2.547: dhcp6 solicit
22:39:24.844781 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:39:25.726337 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:39:26.032780 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:26.182197 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:26.210161 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:26.489925 IP 10.98.6.191.netbios-dgm > 10.98.6.255.netbios-dgm: NBT UDP PACKET(138)
22:39:27.712808 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:39:28.734382 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:39:29.057832 IP anttoni-laptop.local.51543 > ad2.humak.local.domain: 25680+ PTR? 215.14.98.10.in-addr.arpa. (43)
22:39:30.237722 ARP, Request who-has 10.98.6.63 tell 10.98.6.60, length 46
22:39:30.345762 ARP, Request who-has 10.98.6.60 tell 10.98.6.63, length 46
22:39:31.245983 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:31.275698 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:31.306303 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:31.729492 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:39:32.114700 IPX c78a8cc5.00:0e:7f:e5:30:f1.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '000E7FE530F180DZNPIE530F1[|ipx 64]
22:39:32.115607 (NOV-ETHII) IPX 07012000.00:0e:7f:e5:30:f1.0452 > 07012000.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '000E7FE530F181DZNPIE530F1[|ipx 64]
22:39:32.116198 (NOV-ETHII) IPX eef7dd94.00:0e:7f:e5:30:f1.0452 > eef7dd94.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '000E7FE530F182DZNPIE530F1[|ipx 64]
22:39:32.507539 IP6 fe80::19c8:116c:7fad:f69c.546 > ff02::1:2.547: dhcp6 solicit
22:39:32.797198 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:39:34.062931 IP anttoni-laptop.local.51876 > 10.98.14.215.domain: 25680+ PTR? 215.14.98.10.in-addr.arpa. (43)
22:39:34.699819 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:35.061639 IP anttoni-laptop.local > 10.255.255.255: ICMP echo request, id 0, seq 0, length 8
22:39:35.397445 00:19:4b:ab:51:3f (oui Unknown) > Broadcast Null Supervisory, Receiver not Ready, rcv seq 64, Flags [Poll], length 46
22:39:35.411635 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:19:4b:ab:51:3f (oui Unknown), length 265
22:39:35.433058 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:19:4b:ab:51:3f (oui Unknown), length 273
22:39:36.630282 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:36.663353 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:36.699825 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:37.909399 ARP, Request who-has 10.98.6.191 tell 10.98.6.60, length 46
22:39:37.918867 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:39:39.068050 IP anttoni-laptop.local.51543 > ad2.humak.local.domain: 25680+ PTR? 215.14.98.10.in-addr.arpa. (43)
22:39:39.574909 IPX c78a8cc5.00:10:83:2b:b7:91.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '0010832BB79180CXNPI2BB791[|ipx 64]
22:39:39.575635 (NOV-ETHII) IPX 07012000.00:10:83:2b:b7:91.0452 > 07012000.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '0010832BB79181CXNPI2BB791[|ipx 64]
22:39:39.576321 (NOV-ETHII) IPX eef7dd94.00:10:83:2b:b7:91.0452 > eef7dd94.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '0010832BB79182CXNPI2BB791[|ipx 64]
22:39:40.674619 ARP, Request who-has 10.98.6.39 (Broadcast) tell 10.98.6.39, length 46
22:39:41.684502 ARP, Request who-has 10.98.6.39 (Broadcast) tell 10.98.6.39, length 46
22:39:42.213169 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:42.253523 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:42.766967 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:44.173609 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 215.14.98.10.in-addr.arpa. (43)
22:39:44.665498 IP 10.98.6.14.netbios-dgm > 10.98.6.255.netbios-dgm: NBT UDP PACKET(138)
22:39:44.672770 ARP, Request who-has 10.98.6.14 tell anttoni-laptop.local, length 46
22:39:44.977903 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:39:45.174974 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 215.14.98.10.in-addr.arpa. (43)
22:39:47.177372 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 215.14.98.10.in-addr.arpa. (43)
22:39:47.697188 IP6 fe80::225:b3ff:feec:73b6.546 > ff02::1:2.547: dhcp6 solicit
22:39:47.717189 ARP, Request who-has 10.98.6.192 tell 10.98.6.60, length 46
22:39:47.789648 ARP, Request who-has 10.98.6.60 tell 10.98.6.192, length 46
22:39:47.813656 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:47.841476 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:47.869923 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:48.368791 ARP, Request who-has 10.98.6.60 tell 10.98.6.192, length 46
22:39:48.509097 IP6 fe80::19c8:116c:7fad:f69c.546 > ff02::1:2.547: dhcp6 solicit
22:39:49.075733 IP anttoni-laptop.local.34917 > 10.98.14.215.domain: 14740+ PTR? 53.6.98.10.in-addr.arpa. (41)
22:39:49.370312 ARP, Request who-has 10.98.6.60 tell 10.98.6.192, length 46
22:39:49.847100 IPX c78a8cc5.00:80:91:51:32:73.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_05321331[|ipx 64]
22:39:50.043392 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:39:50.460611 IPX c78a8cc5.00:80:91:6b:56:76.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_07034486[|ipx 64]
22:39:52.905688 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:52.933466 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:52.959782 (NOV-ETHII) IPX 07012000.00:21:5e:4e:ac:dc.0452 > 07012000.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp FileServer 'ALKIO[|ipx 448]
22:39:52.959796 IPX c78a8cc5.00:21:5e:4e:ac:dc.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp FileServer 'ALKIO[|ipx 448]
22:39:52.959805 (NOV-ETHII) IPX eef7dd94.00:21:5e:4e:ac:dc.0452 > eef7dd94.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp FileServer 'ALKIO[|ipx 448]
22:39:52.964500 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:53.069607 (NOV-ETHII) IPX 07012000.00:21:5e:4e:ac:dc.0452 > 07012000.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp 0293 'ALKIO[|ipx 448]
22:39:53.069620 IPX c78a8cc5.00:21:5e:4e:ac:dc.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp 0293 'ALKIO[|ipx 320]
22:39:53.069628 (NOV-ETHII) IPX eef7dd94.00:21:5e:4e:ac:dc.0452 > eef7dd94.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp 0293 'ALKIO[|ipx 448]
22:39:54.072984 ARP, Request who-has 10.98.6.1 tell anttoni-laptop.local, length 28
22:39:54.073649 ARP, Reply 10.98.6.1 is-at 00:23:5e:37:47:40 (oui Unknown), length 46
22:39:54.080905 IP anttoni-laptop.local.54555 > ad2.humak.local.domain: 14740+ PTR? 53.6.98.10.in-addr.arpa. (41)
22:39:54.090061 IP ad2.humak.local.domain > anttoni-laptop.local.54555: 14740 NXDomain 0/1/0 (118)
22:39:54.190622 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 53.6.98.10.in-addr.arpa. (41)
22:39:54.190784 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0*- [0q] 1/0/0 (Cache flush) PTR[|domain]
22:39:54.191161 IP anttoni-laptop.local.46236 > 10.98.14.215.domain: 4284+ PTR? 255.6.98.10.in-addr.arpa. (42)
22:39:54.205384 IP 10.98.14.215.domain > anttoni-laptop.local.46236: 4284 NXDomain* 0/1/0 (119)
22:39:54.305991 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.6.98.10.in-addr.arpa. (42)
22:39:55.306600 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.6.98.10.in-addr.arpa. (42)
22:39:55.312098 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:39:57.308944 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.6.98.10.in-addr.arpa. (42)
22:39:58.014356 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:58.083979 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:58.129552 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:39:59.208298 IP anttoni-laptop.local.43918 > 10.98.14.215.domain: 13546+ PTR? 17.6.98.10.in-addr.arpa. (41)
22:39:59.222542 IP 10.98.14.215.domain > anttoni-laptop.local.43918: 13546 NXDomain* 0/1/0 (118)
22:39:59.323040 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 17.6.98.10.in-addr.arpa. (41)
22:39:59.860448 00:00:00:00:00:00 (oui Ethernet) > Broadcast, RRCP-0x03 query
22:40:00.324428 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 17.6.98.10.in-addr.arpa. (41)
22:40:01.244525 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:40:02.325862 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 17.6.98.10.in-addr.arpa. (41)
22:40:03.195008 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:03.235148 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:03.262670 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:04.225377 IP anttoni-laptop.local.40077 > 10.98.14.215.domain: 51377+ PTR? 1.6.98.10.in-addr.arpa. (40)
22:40:04.239091 IP 10.98.14.215.domain > anttoni-laptop.local.40077: 51377 NXDomain* 0/1/0 (117)
22:40:04.339781 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.6.98.10.in-addr.arpa. (40)
22:40:05.341174 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.6.98.10.in-addr.arpa. (40)
22:40:05.458471 00:19:4b:ab:51:3f (oui Unknown) > Broadcast Null Supervisory, Receiver not Ready, rcv seq 64, Flags [Poll], length 46
22:40:05.470408 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:19:4b:ab:51:3f (oui Unknown), length 265
22:40:05.492953 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:19:4b:ab:51:3f (oui Unknown), length 273
22:40:06.518380 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:40:07.342628 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 1.6.98.10.in-addr.arpa. (40)
22:40:08.293123 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:08.362363 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:08.390808 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:09.241999 IP anttoni-laptop.local.56447 > 10.98.14.215.domain: 39732+ PTR? 58.6.98.10.in-addr.arpa. (41)
22:40:09.256267 IP 10.98.14.215.domain > anttoni-laptop.local.56447: 39732 NXDomain* 0/1/0 (118)
22:40:09.356733 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 58.6.98.10.in-addr.arpa. (41)
22:40:10.358077 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 58.6.98.10.in-addr.arpa. (41)
22:40:12.359537 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 58.6.98.10.in-addr.arpa. (41)
22:40:12.443212 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:40:13.319710 ARP, Request who-has 10.98.6.1 tell opisto.local, length 46
22:40:13.398838 ARP, Request who-has 10.98.6.16 tell 10.98.6.177, length 46
22:40:13.426615 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:13.469704 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:13.503544 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:13.506485 00:19:4b:ab:51:80 (oui Unknown) > Broadcast Null Supervisory, Receiver not Ready, rcv seq 64, Flags [Poll], length 46
22:40:14.070230 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/2 (Cache flush) PTR[|domain]
22:40:14.071614 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/2[|domain]
22:40:14.257246 IP anttoni-laptop.local.37270 > 10.98.14.215.domain: 28134+ PTR? 217.14.98.10.in-addr.arpa. (43)
22:40:14.265673 IP 10.98.14.215.domain > anttoni-laptop.local.37270: 28134* 1/0/0 (72)
22:40:14.265924 IP anttoni-laptop.local.56691 > 10.98.14.215.domain: 46951+ PTR? 16.6.98.10.in-addr.arpa. (41)
22:40:14.279248 IP 10.98.14.215.domain > anttoni-laptop.local.56691: 46951 NXDomain* 0/1/0 (118)
22:40:14.371095 IP iPhone.local.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QU)? iPhone.local. ANY (QU)? iPhone.local. (80)
22:40:14.372932 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0 [2q] [2n][|domain]
22:40:14.380481 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 16.6.98.10.in-addr.arpa. (41)
22:40:14.609353 IP iPhone.local.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QM)? iPhone.local. ANY (QM)? iPhone.local. (80)
22:40:14.611003 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0 [2q] [2n][|domain]
22:40:14.920904 IP iPhone.local.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QM)? iPhone.local. ANY (QM)? iPhone.local. (80)
22:40:14.925696 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0 [2q] [2n][|domain]
22:40:15.091809 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/2 (Cache flush) PTR[|domain]
22:40:15.099216 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/2[|domain]
22:40:15.352178 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/1 (Cache flush) A 10.98.6.184, (88)
22:40:15.353672 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/1[|domain]
22:40:15.381470 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 16.6.98.10.in-addr.arpa. (41)
22:40:16.163110 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/1 (Cache flush) A 10.98.6.184, (88)
22:40:16.165106 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/1[|domain]
22:40:17.063160 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/2 (Cache flush) PTR[|domain]
22:40:17.070094 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/2[|domain]
22:40:17.381103 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 16.6.98.10.in-addr.arpa. (41)
22:40:17.419778 ARP, Request who-has 10.98.6.1 tell 10.98.6.192, length 46
22:40:17.546218 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:40:17.709753 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:40:18.163887 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/1 (Cache flush) A 10.98.6.184, (88)
22:40:18.165850 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/1[|domain]
22:40:18.534234 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:18.563025 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:18.592781 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:18.907756 IP 10.98.6.60.6771 > 239.192.152.143.6771: UDP, length 119
22:40:19.280847 IP anttoni-laptop.local.40103 > 10.98.14.215.domain: 17403+ PTR? 255.255.255.255.in-addr.arpa. (46)
22:40:19.289805 IP 10.98.14.215.domain > anttoni-laptop.local.40103: 17403 NXDomain* 0/1/0 (124)
22:40:19.390314 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.255.255.255.in-addr.arpa. (46)
22:40:19.569426 ARP, Request who-has 10.98.6.16 tell 10.98.6.177, length 46
22:40:19.682198 ARP, Request who-has 10.98.6.126 tell 10.98.6.60, length 46
22:40:19.684231 ARP, Request who-has 10.98.6.60 tell 10.98.6.126, length 46
22:40:19.847512 IPX c78a8cc5.00:80:91:51:32:73.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_05321331[|ipx 64]
22:40:20.391709 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.255.255.255.in-addr.arpa. (46)
22:40:20.460002 IPX c78a8cc5.00:80:91:6b:56:76.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_07034486[|ipx 64]
22:40:20.504072 IP6 fe80::19c8:116c:7fad:f69c.546 > ff02::1:2.547: dhcp6 solicit
22:40:20.709990 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:40:21.064966 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 4/0/3 (Cache flush) PTR[|domain]
22:40:21.067071 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 4/0/3[|domain]
22:40:22.392167 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.255.255.255.in-addr.arpa. (46)
22:40:22.654981 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:40:22.889806 (NOV-ETHII) IPX 07012000.00:21:5e:4e:ac:dc.0453 > 07012000.ff:ff:ff:ff:ff:ff.0453: ipx-rip-resp 19088743/1.2 4009221524/1.2 3347745989/1.2
22:40:22.889828 IPX c78a8cc5.00:21:5e:4e:ac:dc.0453 > c78a8cc5.ff:ff:ff:ff:ff:ff.0453: ipx-rip-resp 117514240/1.2 19088743/1.2 4009221524/1.2
22:40:22.889836 (NOV-ETHII) IPX eef7dd94.00:21:5e:4e:ac:dc.0453 > eef7dd94.ff:ff:ff:ff:ff:ff.0453: ipx-rip-resp 117514240/1.2 19088743/1.2 3347745989/1.2
22:40:23.637428 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:23.704116 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:23.711090 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:40:23.789611 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:24.292550 IP anttoni-laptop.local.47276 > 10.98.14.215.domain: 33026+ PTR? 0.0.0.0.in-addr.arpa. (38)
22:40:24.301495 IP 10.98.14.215.domain > anttoni-laptop.local.47276: 33026 NXDomain* 0/1/0 (114)
22:40:24.401949 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 0.0.0.0.in-addr.arpa. (38)
22:40:25.403293 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 0.0.0.0.in-addr.arpa. (38)
22:40:25.608462 IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 00000000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:25.608687 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 07012000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:25.608700 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > eef7dd94.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:25.676027 ARP, Request who-has 10.98.6.16 tell 10.98.6.177, length 46
22:40:26.380928 IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 00000000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:26.381449 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 07012000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:26.381467 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > eef7dd94.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:26.491281 IP 10.98.6.191.netbios-dgm > 10.98.6.255.netbios-dgm: NBT UDP PACKET(138)
22:40:26.749750 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:40:27.153363 IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 00000000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:27.153496 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 07012000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:27.153509 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > eef7dd94.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:27.260505 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/2 (Cache flush) PTR[|domain]
22:40:27.261224 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/2[|domain]
22:40:27.404089 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 0.0.0.0.in-addr.arpa. (38)
22:40:27.616810 IP iPhone.local.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QU)? iPhone.local. ANY (QU)? iPhone.local. (80)
22:40:27.617691 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0 [2q] [2n][|domain]
22:40:27.825879 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:40:27.861185 IP iPhone.local.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QM)? iPhone.local. ANY (QM)? iPhone.local. (80)
22:40:27.887650 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0 [2q] [2n][|domain]
22:40:27.980992 IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 00000000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:27.981694 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > eef7dd94.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:27.981705 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 07012000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:28.112326 IP iPhone.local.mdns > 224.0.0.251.mdns: 0 [2q] [2n] ANY (QM)? iPhone.local. ANY (QM)? iPhone.local. (80)
22:40:28.114171 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0 [2q] [2n][|domain]
22:40:28.242462 IP 10.98.6.84.netbios-dgm > 10.98.6.255.netbios-dgm: NBT UDP PACKET(138)
22:40:28.249512 ARP, Request who-has 10.98.6.84 tell anttoni-laptop.local, length 46
22:40:28.256090 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/2 (Cache flush) PTR[|domain]
22:40:28.257814 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/2[|domain]
22:40:28.361625 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/1 (Cache flush) A 10.98.6.184, (88)
22:40:28.362055 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/1[|domain]
22:40:28.753424 IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 00000000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:28.754070 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 07012000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:28.754082 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > eef7dd94.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:28.876732 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:28.913571 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:28.950898 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:29.292475 ARP, Request who-has 10.98.6.1 tell anttoni-laptop.local, length 28
22:40:29.293046 ARP, Reply 10.98.6.1 is-at 00:23:5e:37:47:40 (oui Unknown), length 46
22:40:29.303326 IP anttoni-laptop.local.43927 > 10.98.14.215.domain: 56246+ PTR? 251.0.0.224.in-addr.arpa. (42)
22:40:29.369692 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/1 (Cache flush) A 10.98.6.184, (88)
22:40:29.372634 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/1[|domain]
22:40:29.525881 IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 00000000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:29.526181 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > 07012000.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:29.526193 (NOV-ETHII) IPX c78a8cc5.00:01:01:c4:0e:b8.0455 > eef7dd94.ff:ff:ff:ff:ff:ff.0455: ipx-netbios 50
22:40:29.544008 IP 10.98.14.215.domain > anttoni-laptop.local.43927: 56246 NXDomain*- 0/1/0 (100)
22:40:29.644491 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
22:40:29.786074 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:40:30.257742 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/2 (Cache flush) PTR[|domain]
22:40:30.290074 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/2[|domain]
22:40:30.645658 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
22:40:31.369450 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 2/0/1 (Cache flush) A 10.98.6.184, (88)
22:40:31.385601 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 2/0/1[|domain]
22:40:31.814648 ARP, Request who-has 10.98.6.16 tell 10.98.6.177, length 46
22:40:32.300099 IPX c78a8cc5.00:0e:7f:e5:30:f1.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '000E7FE530F180DZNPIE530F1[|ipx 64]
22:40:32.301380 (NOV-ETHII) IPX 07012000.00:0e:7f:e5:30:f1.0452 > 07012000.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '000E7FE530F181DZNPIE530F1[|ipx 64]
22:40:32.302004 (NOV-ETHII) IPX eef7dd94.00:0e:7f:e5:30:f1.0452 > eef7dd94.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '000E7FE530F182DZNPIE530F1[|ipx 64]
22:40:32.647248 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
22:40:32.750948 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:40:32.998400 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:40:34.019804 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:34.061162 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:34.088153 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:34.257439 IP iPhone.local.mdns > 224.0.0.251.mdns: 0*- [0q] 4/0/3 (Cache flush) PTR[|domain]
22:40:34.261240 IP6 fe80::5a55:caff:fed9:d8a.mdns > ff02::fb.mdns: 0*- [0q] 4/0/3[|domain]
22:40:34.545375 IP anttoni-laptop.local.56431 > 10.98.14.215.domain: 65135+ PTR? 184.6.98.10.in-addr.arpa. (42)
22:40:34.559201 IP 10.98.14.215.domain > anttoni-laptop.local.56431: 65135 NXDomain* 0/1/0 (119)
22:40:34.559687 IP anttoni-laptop.local.34440 > 10.98.14.215.domain: 1459+[|domain]
22:40:34.671038 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:34.839816 IP 10.98.14.215.domain > anttoni-laptop.local.34440: 1459 NXDomain*-[|domain]
22:40:34.840101 IP anttoni-laptop.local.35146 > 10.98.14.215.domain: 43062+[|domain]
22:40:35.517973 00:19:4b:ab:51:3f (oui Unknown) > Broadcast Null Supervisory, Receiver not Ready, rcv seq 64, Flags [Poll], length 46
22:40:35.526345 ARP, Request who-has 10.98.6.1 tell 10.98.6.51, length 46
22:40:35.530434 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:19:4b:ab:51:3f (oui Unknown), length 265
22:40:35.546037 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:19:4b:ab:51:3f (oui Unknown), length 273
22:40:38.048271 IP 10.98.14.215.domain > anttoni-laptop.local.35146: 43062 NXDomain*-[|domain]
22:40:38.048871 IP anttoni-laptop.local.52961 > 10.98.14.215.domain: 39869+[|domain]
22:40:38.216293 ARP, Request who-has NPI83BC9D.local tell 10.98.6.177, length 46
22:40:39.570606 ARP, Request who-has 10.98.6.1 tell 10.98.6.62, length 46
22:40:39.573587 IPX c78a8cc5.00:10:83:2b:b7:91.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '0010832BB79180CXNPI2BB791[|ipx 64]
22:40:39.574299 (NOV-ETHII) IPX 07012000.00:10:83:2b:b7:91.0452 > 07012000.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '0010832BB79181CXNPI2BB791[|ipx 64]
22:40:39.575007 (NOV-ETHII) IPX eef7dd94.00:10:83:2b:b7:91.0452 > eef7dd94.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp IntelNetport2/HP JetDirect/HP Quicksilver '0010832BB79182CXNPI2BB791[|ipx 64]
22:40:39.733193 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:39.833205 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:39.872213 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:41.054449 ARP, Request who-has 10.98.6.39 (Broadcast) tell 10.98.6.39, length 46
22:40:41.150679 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:40:41.546261 IP 10.98.14.215.domain > anttoni-laptop.local.52961: 39869 NXDomain*-[|domain]
22:40:41.546539 IP anttoni-laptop.local.56079 > 10.98.14.215.domain: 12629+[|domain]
22:40:41.827007 IP 10.98.14.215.domain > anttoni-laptop.local.56079: 12629 NXDomain*-[|domain]
22:40:41.827358 IP anttoni-laptop.local.41496 > 10.98.14.215.domain: 23179+ PTR? 192.6.98.10.in-addr.arpa. (42)
22:40:41.840761 IP 10.98.14.215.domain > anttoni-laptop.local.41496: 23179 NXDomain* 0/1/0 (119)
22:40:41.941448 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 192.6.98.10.in-addr.arpa. (42)
22:40:42.063542 ARP, Request who-has 10.98.6.39 (Broadcast) tell 10.98.6.39, length 46
22:40:42.942877 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 192.6.98.10.in-addr.arpa. (42)
22:40:43.416585 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 442
22:40:43.416610 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 452
22:40:43.416817 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 513
22:40:43.416830 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 523
22:40:43.417464 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 499
22:40:43.417476 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 509
22:40:43.417602 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 485
22:40:43.417614 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 495
22:40:43.417764 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 433
22:40:43.417777 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 443
22:40:43.417785 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 497
22:40:43.417887 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 507
22:40:43.644784 IP6 fe80::f5b0:fc53:ad06:f96.546 > ff02::1:2.547: dhcp6 solicit
22:40:44.644947 IP6 fe80::f5b0:fc53:ad06:f96.546 > ff02::1:2.547: dhcp6 solicit
22:40:44.919147 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:44.945214 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 192.6.98.10.in-addr.arpa. (42)
22:40:44.952561 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:44.986390 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:46.416463 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 442
22:40:46.416488 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 452
22:40:46.416505 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 513
22:40:46.416577 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 523
22:40:46.417443 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 499
22:40:46.417455 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 509
22:40:46.417576 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 497
22:40:46.417588 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 507
22:40:46.417738 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 433
22:40:46.417749 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 443
22:40:46.417759 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 485
22:40:46.417856 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 495
22:40:46.644965 IP6 fe80::f5b0:fc53:ad06:f96.546 > ff02::1:2.547: dhcp6 solicit
22:40:46.843644 IP anttoni-laptop.local.53941 > 10.98.14.215.domain: 23466+ PTR? 250.255.255.239.in-addr.arpa. (46)
22:40:47.079139 IP 10.98.14.215.domain > anttoni-laptop.local.53941: 23466 NXDomain*- 0/1/0 (103)
22:40:47.161959 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:40:47.179673 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
22:40:48.181068 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
22:40:49.304758 IP 10.98.6.84.netbios-dgm > 10.98.6.255.netbios-dgm: NBT UDP PACKET(138)
22:40:49.305080 IP MFP-07034486.local.netbios-dgm > 10.98.6.255.netbios-dgm: NBT UDP PACKET(138)
22:40:49.305220 IP MFP-05321331.local.netbios-dgm > 10.98.6.255.netbios-dgm: NBT UDP PACKET(138)
22:40:49.315634 ARP, Request who-has MFP-07034486.local tell anttoni-laptop.local, length 46
22:40:49.317928 ARP, Request who-has MFP-05321331.local tell anttoni-laptop.local, length 46
22:40:49.416375 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 442
22:40:49.416389 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 452
22:40:49.416523 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 513
22:40:49.416535 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 523
22:40:49.417371 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 499
22:40:49.417383 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 509
22:40:49.417509 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 485
22:40:49.417522 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 495
22:40:49.417530 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 433
22:40:49.417630 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 443
22:40:49.417764 IP Dread-PC.local.1900 > 239.255.255.250.1900: UDP, length 497
22:40:49.417777 IP6 fe80::3ce2:870c:cba3:fefb.1900 > ff02::c.1900: UDP, length 507
22:40:49.847911 IPX c78a8cc5.00:80:91:51:32:73.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_05321331[|ipx 64]
22:40:50.043383 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:50.076765 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:50.108653 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:50.182491 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
22:40:50.459414 IPX c78a8cc5.00:80:91:6b:56:76.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_07034486[|ipx 64]
22:40:50.645049 IP6 fe80::f5b0:fc53:ad06:f96.546 > ff02::1:2.547: dhcp6 solicit
22:40:51.339843 IP6 fe80::225:b3ff:feec:d4fe.546 > ff02::1:2.547: dhcp6 solicit
22:40:52.081889 IP anttoni-laptop.local.34774 > 10.98.14.215.domain: 10454+[|domain]
22:40:52.231510 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:40:52.827291 ARP, Request who-has Dread-PC.local tell 10.98.6.60, length 46
22:40:52.829778 ARP, Request who-has 10.98.6.60 tell Dread-PC.local, length 46
22:40:52.930208 (NOV-ETHII) IPX 07012000.00:21:5e:4e:ac:dc.0452 > 07012000.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp FileServer 'ALKIO[|ipx 448]
22:40:52.930226 IPX c78a8cc5.00:21:5e:4e:ac:dc.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp FileServer 'ALKIO[|ipx 448]
22:40:52.930234 (NOV-ETHII) IPX eef7dd94.00:21:5e:4e:ac:dc.0452 > eef7dd94.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp FileServer 'ALKIO[|ipx 448]
22:40:53.040040 (NOV-ETHII) IPX 07012000.00:21:5e:4e:ac:dc.0452 > 07012000.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp 0293 'ALKIO[|ipx 448]
22:40:53.040054 IPX c78a8cc5.00:21:5e:4e:ac:dc.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp 0293 'ALKIO[|ipx 320]
22:40:53.040062 (NOV-ETHII) IPX eef7dd94.00:21:5e:4e:ac:dc.0452 > eef7dd94.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp 0293 'ALKIO[|ipx 448]
22:40:54.280608 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 1c:4b:d6:6e:54:eb (oui Unknown), length 304
22:40:54.286929 IP6 fe80::b9db:be76:e3e2:2aea.546 > ff02::1:2.547: dhcp6 solicit
22:40:54.357647 ARP, Request who-has 10.98.6.1 tell 10.98.6.191, length 46
22:40:54.508853 ARP, Request who-has 10.98.6.191 tell 0.0.0.0, length 46
22:40:54.509191 IP 10.98.6.191 > igmp.mcast.net: igmp v3 report, 1 group record(s)
22:40:54.509466 IP6 :: > ff02::1:ffe2:2aea: ICMP6, neighbor solicitation, who has fe80::b9db:be76:e3e2:2aea, length 24
22:40:54.509727 IP6 fe80::b9db:be76:e3e2:2aea > ip6-allrouters: ICMP6, router solicitation, length 16
22:40:54.510038 IP6 fe80::b9db:be76:e3e2:2aea > ff02::16: HBH ICMP6, multicast listener report v2, 2 group record(s), length 48
22:40:54.633720 IP 10.98.6.191.57450 > 239.255.255.250.1900: UDP, length 133
22:40:54.738008 ARP, Request who-has 10.98.6.191 tell 10.98.6.168, length 46
22:40:55.000100 IP 10.98.6.191 > igmp.mcast.net: igmp v3 report, 1 group record(s)
22:40:55.000448 IP6 fe80::b9db:be76:e3e2:2aea > ff02::16: HBH ICMP6, multicast listener report v2, 2 group record(s), length 48
22:40:55.146509 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:55.177323 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:55.208991 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:40:55.274000 IP6 fe80::b9db:be76:e3e2:2aea.546 > ff02::1:2.547: dhcp6 solicit
22:40:55.490780 ARP, Request who-has 10.98.6.191 tell 0.0.0.0, length 46
22:40:55.545010 ARP, Request who-has 10.98.6.1 tell 10.98.6.191, length 46
22:40:55.563417 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 90:4c:e5:a4:c1:ae (oui Unknown), length 306
22:40:55.573180 IP 10.98.6.1.bootps > 255.255.255.255.bootpc: BOOTP/DHCP, Reply, length 309
22:40:55.671700 IP 10.98.6.192 > igmp.mcast.net: igmp v3 report, 1 group record(s)
22:40:55.685610 IP 10.98.6.192 > igmp.mcast.net: igmp v3 report, 1 group record(s)
22:40:55.691956 IP 10.98.6.192 > igmp.mcast.net: igmp v3 report, 1 group record(s)
22:40:55.692250 ARP, Request who-has 10.98.6.1 tell 10.98.6.192, length 46
22:40:55.698830 IP 10.98.6.192 > igmp.mcast.net: igmp v3 report, 1 group record(s)
22:40:55.699371 IP 10.98.6.192.65317 > 224.0.0.252.hostmon: UDP, length 26
22:40:55.804295 IP 10.98.6.192.65317 > 224.0.0.252.hostmon: UDP, length 26
22:40:55.870138 ARP, Request who-has 10.98.6.192 tell 0.0.0.0, length 46
22:40:55.872757 IP 10.98.6.192 > igmp.mcast.net: igmp v3 report, 2 group record(s)
22:40:55.968334 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:40:56.368591 IP 10.98.6.192 > igmp.mcast.net: igmp v3 report, 1 group record(s)
22:40:56.490687 ARP, Request who-has 10.98.6.191 tell 0.0.0.0, length 46
22:40:56.868319 ARP, Request who-has 10.98.6.192 tell 0.0.0.0, length 46
22:40:56.894422 ARP, Request who-has 10.98.6.1 tell 10.98.6.192, length 46
22:40:57.087051 IP anttoni-laptop.local.49658 > ad2.humak.local.domain: 10454+[|domain]
22:40:57.252737 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:40:57.272282 IP6 fe80::b9db:be76:e3e2:2aea.546 > ff02::1:2.547: dhcp6 solicit
22:40:57.528461 ARP, Request who-has 10.98.6.1 tell 10.98.6.191, length 46
22:40:57.636008 IP 10.98.6.191.57450 > 239.255.255.250.1900: UDP, length 133
22:40:57.868307 ARP, Request who-has 10.98.6.192 tell 0.0.0.0, length 46
22:40:58.491338 IP6 fe80::b9db:be76:e3e2:2aea > ip6-allrouters: ICMP6, router solicitation, length 16
22:40:58.645205 IP6 fe80::f5b0:fc53:ad06:f96.546 > ff02::1:2.547: dhcp6 solicit
22:40:58.906013 ARP, Request who-has 10.98.6.1 tell 10.98.6.192, length 46
22:40:58.968926 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:40:59.883671 IP 10.98.6.192.60867 > 224.0.0.252.hostmon: UDP, length 28
22:40:59.884149 IP 10.98.6.192.61597 > 224.0.0.252.hostmon: UDP, length 28
22:40:59.886027 IP 10.98.6.192.53018 > 224.0.0.252.hostmon: UDP, length 28
22:40:59.984489 IP 10.98.6.192.61597 > 224.0.0.252.hostmon: UDP, length 28
22:40:59.985226 IP 10.98.6.192.60867 > 224.0.0.252.hostmon: UDP, length 28
22:40:59.988300 IP 10.98.6.192.53018 > 224.0.0.252.hostmon: UDP, length 28
22:41:00.183349 IP 10.98.6.192.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:41:00.183694 IP 10.98.6.192.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:41:00.185359 IP 10.98.6.192.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:41:00.244261 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:00.274662 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:00.310761 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:00.467055 ARP, Request who-has 10.98.6.7 tell 10.98.6.204, length 46
22:41:00.641736 IP 10.98.6.191.57450 > 239.255.255.250.1900: UDP, length 133
22:41:00.932813 IP 10.98.6.192.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:41:00.933865 IP 10.98.6.192.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:41:00.936367 IP 10.98.6.192.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:41:01.273341 IP6 fe80::b9db:be76:e3e2:2aea.546 > ff02::1:2.547: dhcp6 solicit
22:41:01.683195 IP 10.98.6.192.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:41:01.683910 IP 10.98.6.192.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:41:01.684967 IP 10.98.6.192.netbios-ns > 10.98.6.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
22:41:01.969826 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:41:02.084457 ARP, Request who-has 10.98.6.1 tell anttoni-laptop.local, length 28
22:41:02.084995 ARP, Reply 10.98.6.1 is-at 00:23:5e:37:47:40 (oui Unknown), length 46
22:41:02.092164 IP anttoni-laptop.local.34774 > 10.98.14.215.domain: 10454+[|domain]
22:41:02.101151 IP 10.98.14.215.domain > anttoni-laptop.local.34774: 10454 NXDomain[|domain]
22:41:02.101405 IP anttoni-laptop.local.42529 > 10.98.14.215.domain: 60705+ PTR? 30.6.98.10.in-addr.arpa. (41)
22:41:02.115785 IP 10.98.14.215.domain > anttoni-laptop.local.42529: 60705 NXDomain* 0/1/0 (118)
22:41:02.217678 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 30.6.98.10.in-addr.arpa. (41)
22:41:02.218485 IP NPI83BC9D.local.mdns > 224.0.0.251.mdns: 0*- [0q] 1/0/0 (Cache flush) PTR[|domain]
22:41:02.218840 IP anttoni-laptop.local.59950 > 10.98.14.215.domain: 49678+ PTR? 36.6.98.10.in-addr.arpa. (41)
22:41:02.233480 IP 10.98.14.215.domain > anttoni-laptop.local.59950: 49678 NXDomain* 0/1/0 (118)
22:41:02.272093 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:41:02.297475 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:41:02.334158 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 36.6.98.10.in-addr.arpa. (41)
22:41:02.334832 IP NPIECD4FE.local.mdns > 224.0.0.251.mdns: 0*- [0q] 1/0/0 (Cache flush) PTR[|domain]
22:41:02.335094 IP6 fe80::225:b3ff:feec:d4fe.mdns > ff02::fb.mdns: 0*- [0q] 1/0/0 (64)
22:41:02.335309 IP anttoni-laptop.local.38148 > 10.98.14.215.domain: 30548+ PTR? 90.6.98.10.in-addr.arpa. (41)
22:41:02.348950 IP 10.98.14.215.domain > anttoni-laptop.local.38148: 30548 NXDomain* 0/1/0 (118)
22:41:02.449902 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 90.6.98.10.in-addr.arpa. (41)
22:41:02.492665 IP6 fe80::b9db:be76:e3e2:2aea > ip6-allrouters: ICMP6, router solicitation, length 16
22:41:03.450492 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 90.6.98.10.in-addr.arpa. (41)
22:41:03.677520 IP 10.98.6.191.57450 > 239.255.255.250.1900: UDP, length 133
22:41:05.010655 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:41:05.349160 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:05.376316 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:05.403025 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:05.452773 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 90.6.98.10.in-addr.arpa. (41)
22:41:05.577194 00:19:4b:ab:51:3f (oui Unknown) > Broadcast Null Supervisory, Receiver not Ready, rcv seq 64, Flags [Poll], length 46
22:41:05.589088 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:19:4b:ab:51:3f (oui Unknown), length 265
22:41:05.608564 IP 0.0.0.0.bootpc > 255.255.255.255.bootps: BOOTP/DHCP, Request from 00:19:4b:ab:51:3f (oui Unknown), length 273
22:41:06.678751 IP 10.98.6.191.57450 > 239.255.255.250.1900: UDP, length 133
22:41:07.308088 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:41:07.352478 IP anttoni-laptop.local.46964 > 10.98.14.215.domain: 13256+ PTR? 191.6.98.10.in-addr.arpa. (42)
22:41:07.362589 IP 10.98.14.215.domain > anttoni-laptop.local.46964: 13256 NXDomain 0/1/0 (119)
22:41:07.463197 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 191.6.98.10.in-addr.arpa. (42)
22:41:08.008460 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:41:08.464610 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 191.6.98.10.in-addr.arpa. (42)
22:41:09.284184 IP6 fe80::b9db:be76:e3e2:2aea.546 > ff02::1:2.547: dhcp6 solicit
22:41:09.683639 IP 10.98.6.191.57450 > 239.255.255.250.1900: UDP, length 133
22:41:10.433307 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:10.466055 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 191.6.98.10.in-addr.arpa. (42)
22:41:10.467451 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:10.497831 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:11.009457 IP 10.98.6.192.56555 > 239.255.255.250.1900: UDP, length 133
22:41:12.327267 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:41:12.365503 IP anttoni-laptop.local.41465 > 10.98.14.215.domain: 374+ PTR? 63.6.98.10.in-addr.arpa. (41)
22:41:12.379478 IP 10.98.14.215.domain > anttoni-laptop.local.41465: 374 NXDomain* 0/1/0 (118)
22:41:12.480177 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 63.6.98.10.in-addr.arpa. (41)
22:41:13.386801 IP anttoni-laptop.local > 10.255.255.255: ICMP echo request, id 0, seq 0, length 8
22:41:13.481564 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 63.6.98.10.in-addr.arpa. (41)
22:41:13.506988 ARP, Request who-has anttoni-laptop.local tell 10.98.6.168, length 46
22:41:13.507006 ARP, Reply anttoni-laptop.local is-at 48:5b:39:81:bc:8f (oui Unknown), length 28
22:41:13.572218 IP 10.98.6.168.netbios-ns > anttoni-laptop.local.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; UNICAST
22:41:13.572247 IP anttoni-laptop.local > 10.98.6.168: ICMP anttoni-laptop.local udp port netbios-ns unreachable, length 86
22:41:14.645417 IP6 fe80::f5b0:fc53:ad06:f96.546 > ff02::1:2.547: dhcp6 solicit
22:41:15.482994 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 63.6.98.10.in-addr.arpa. (41)
22:41:15.532701 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:15.566887 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:15.595529 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:17.382563 IP anttoni-laptop.local.38161 > 10.98.14.215.domain: 26832+ PTR? 255.255.255.10.in-addr.arpa. (45)
22:41:17.396209 IP 10.98.14.215.domain > anttoni-laptop.local.38161: 26832 NXDomain* 0/1/0 (122)
22:41:17.401694 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:41:17.496881 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.255.255.10.in-addr.arpa. (45)
22:41:18.497589 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.255.255.10.in-addr.arpa. (45)
22:41:18.568491 ARP, Request who-has 10.98.6.168 tell anttoni-laptop.local, length 28
22:41:18.571276 ARP, Reply 10.98.6.168 is-at 70:f1:a1:43:7f:07 (oui Unknown), length 46
22:41:19.848355 IPX c78a8cc5.00:80:91:51:32:73.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_05321331[|ipx 64]
22:41:20.458836 IPX c78a8cc5.00:80:91:6b:56:76.0452 > c78a8cc5.ff:ff:ff:ff:ff:ff.0452: ipx-sap-resp AdvertisingPrintServer 'MFP_07034486[|ipx 64]
22:41:20.499034 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 255.255.255.10.in-addr.arpa. (45)
22:41:20.635030 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:20.662339 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:20.704499 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:21.599215 ARP, Request who-has 10.98.6.4 tell 10.98.6.1, length 46
22:41:21.599414 IP anttoni-laptop.local.59768 > 10.98.14.215.domain: 441+ PTR? 4.6.98.10.in-addr.arpa. (40)
22:41:21.599425 IP anttoni-laptop.local.42330 > 10.98.14.215.domain: 19627+ PTR? 4.6.98.10.in-addr.arpa. (40)
22:41:21.612762 IP 10.98.14.215.domain > anttoni-laptop.local.59768: 441 NXDomain* 0/1/0 (117)
22:41:21.613689 IP 10.98.14.215.domain > anttoni-laptop.local.42330: 19627 NXDomain* 0/1/0 (117)
22:41:21.714112 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 4.6.98.10.in-addr.arpa. (40)
22:41:22.165526 ARP, Request who-has 10.98.6.1 tell 10.98.6.7, length 46
22:41:22.212179 ARP, Request who-has 10.98.6.1 tell 10.98.6.8, length 46
22:41:22.398476 IP anttoni-laptop.local.56723 > 10.98.14.215.domain: 33777+ PTR? 39.6.98.10.in-addr.arpa. (41)
22:41:22.412198 IP 10.98.14.215.domain > anttoni-laptop.local.56723: 33777 NXDomain* 0/1/0 (118)
22:41:22.479262 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:41:22.512819 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 39.6.98.10.in-addr.arpa. (41)
22:41:22.713305 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 4.6.98.10.in-addr.arpa. (40)
22:41:22.860236 (NOV-ETHII) IPX 07012000.00:21:5e:4e:ac:dc.0453 > 07012000.ff:ff:ff:ff:ff:ff.0453: ipx-rip-resp 19088743/1.2 4009221524/1.2 3347745989/1.2
22:41:22.860252 IPX c78a8cc5.00:21:5e:4e:ac:dc.0453 > c78a8cc5.ff:ff:ff:ff:ff:ff.0453: ipx-rip-resp 117514240/1.2 19088743/1.2 4009221524/1.2
22:41:22.860258 (NOV-ETHII) IPX eef7dd94.00:21:5e:4e:ac:dc.0453 > eef7dd94.ff:ff:ff:ff:ff:ff.0453: ipx-rip-resp 117514240/1.2 19088743/1.2 3347745989/1.2
22:41:23.178125 ARP, Request who-has 10.98.6.1 tell 10.98.6.14, length 46
22:41:23.513375 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 39.6.98.10.in-addr.arpa. (41)
22:41:23.535447 ARP, Request who-has 10.98.6.1 tell 10.98.6.15, length 46
22:41:23.587072 ARP, Request who-has 10.98.6.16 tell 10.98.6.1, length 46
22:41:24.087598 ARP, Request who-has 10.98.6.18 tell 10.98.6.1, length 46
22:41:24.587150 ARP, Request who-has 10.98.6.4 tell 10.98.6.1, length 46
22:41:24.587317 ARP, Request who-has 10.98.6.19 tell 10.98.6.1, length 46
22:41:24.714003 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 4.6.98.10.in-addr.arpa. (40)
22:41:24.804682 ARP, Request who-has 10.98.6.20 tell 10.98.6.1, length 46
22:41:25.073573 ARP, Request who-has 10.98.6.1 tell 10.98.6.22, length 46
22:41:25.275175 IP6 fe80::b9db:be76:e3e2:2aea.546 > ff02::1:2.547: dhcp6 solicit
22:41:25.513576 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 39.6.98.10.in-addr.arpa. (41)
22:41:25.587260 ARP, Request who-has 10.98.6.16 tell 10.98.6.1, length 46
22:41:25.738517 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:25.777105 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:25.778446 IP6 fe80::3ce2:870c:cba3:fefb.546 > ff02::1:2.547: dhcp6 solicit
22:41:25.804884 ARP, Request who-has 10.98.6.1 tell 10.98.6.58, length 46
22:41:25.826686 ARP, Request who-has 10.98.6.27 tell 10.98.6.1, length 46
22:41:26.086599 ARP, Request who-has 10.98.6.18 tell 10.98.6.1, length 46
22:41:26.572464 IP printer.humak.local.59987 > 10.98.6.28.snmp:  GetRequest(26)  system.sysDescr.0
22:41:26.573314 ARP, Request who-has 10.98.6.31 tell 10.98.6.1, length 46
22:41:26.585776 IP printer.humak.local.59993 > 10.98.6.28.snmp:  GetRequest(30)  43.10.2.1.4.1.1
22:41:26.586873 ARP, Request who-has 10.98.6.32 tell 10.98.6.1, length 46
22:41:26.588993 ARP, Request who-has 10.98.6.19 tell 10.98.6.1, length 46
22:41:26.589238 ARP, Request who-has 10.98.6.37 tell 10.98.6.1, length 46
22:41:26.615237 IP anttoni-laptop.local.56270 > 10.98.14.215.domain: 2415+ PTR? 8.6.98.10.in-addr.arpa. (40)
22:41:26.615250 IP anttoni-laptop.local.52487 > 10.98.14.215.domain: 40234+ PTR? 8.6.98.10.in-addr.arpa. (40)
22:41:26.633528 IP 10.98.14.215.domain > anttoni-laptop.local.52487: 40234 NXDomain* 0/1/0 (117)
22:41:26.633546 IP 10.98.14.215.domain > anttoni-laptop.local.56270: 2415 NXDomain* 0/1/0 (117)
22:41:26.639008 ARP, Request who-has 10.98.6.38 tell 10.98.6.1, length 46
22:41:26.734084 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 8.6.98.10.in-addr.arpa. (40)
22:41:26.777594 IP6 fe80::3ce2:870c:cba3:fefb.546 > ff02::1:2.547: dhcp6 solicit
22:41:27.413928 IP anttoni-laptop.local.34568 > 10.98.14.215.domain: 51346+ PTR? 14.6.98.10.in-addr.arpa. (41)
22:41:27.427983 IP 10.98.14.215.domain > anttoni-laptop.local.34568: 51346 NXDomain* 0/1/0 (118)
22:41:27.528613 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 14.6.98.10.in-addr.arpa. (41)
22:41:27.571466 ARP, Request who-has 10.98.6.40 tell 10.98.6.1, length 46
22:41:27.592753 ARP, Request who-has 10.98.6.16 tell 10.98.6.1, length 46
22:41:27.595743 ARP, Request who-has 10.98.6.1 tell 10.98.6.60, length 46
22:41:27.618696 ARP, Request who-has 10.98.6.41 tell 10.98.6.1, length 46
22:41:27.660901 ARP, Request who-has 10.98.6.42 tell 10.98.6.1, length 46
22:41:27.679909 ARP, Request who-has 10.98.6.43 tell 10.98.6.1, length 46
22:41:27.734237 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 8.6.98.10.in-addr.arpa. (40)
22:41:27.789483 ARP, Request who-has 10.98.6.20 tell 10.98.6.1, length 46
22:41:28.086689 ARP, Request who-has 10.98.6.18 tell 10.98.6.1, length 46
22:41:28.165236 ARP, Request who-has 10.98.6.44 tell 10.98.6.1, length 46
22:41:28.297962 IP6 fe80::225:b3ff:feec:73b6.546 > ff02::1:2.547: dhcp6 solicit
22:41:28.529479 IP anttoni-laptop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 14.6.98.10.in-addr.arpa. (41)
22:41:28.586784 ARP, Request who-has 10.98.6.32 tell 10.98.6.1, length 46
22:41:28.587211 ARP, Request who-has 10.98.6.45 tell 10.98.6.1, length 46[/SIZE]

- - - - -
end
- - - - -

---

### Post by Il_Literacy on 2010-11-29
don't know if allowed but bump

---

### Post by Il_Literacy on 2010-11-30
bump

---

