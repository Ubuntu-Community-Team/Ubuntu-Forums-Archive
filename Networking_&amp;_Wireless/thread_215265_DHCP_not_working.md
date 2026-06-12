---
title: "DHCP not working?"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by DigitDuke on 2006-07-13
Hi there,

Being a new to all this manual configuring I might need to rely a bit on your answers on this one.

I installed Ubuntu a few hours ago and I've been struggling to get the Internet working.  At startup I got an error saying that the system thinks my router doesn't have DHCP.  I, however, am connecting on all my computers through DHCP without any configuration to that very same router.

I have a Netopia Cayman 3347W.

When trying to run a **dhclient** I get the following output:

```
Internet Systems Consortium DCHP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:50:da:2d:ee:e4
Sending on   LPF/eth0/00:50:da:2d:ee:e4
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.
```

I altered my [FONT="Courier New"]/etc/network/interfaces[/FONT] file to look like this:

```
# This file describes the network interfaces available on your your system
# and how to activate them. For more information, see interfaces(5)

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# As instructed by howtoforge.com/book/print/1332
auto eth0
iface eth0 inet static
        address 192.168.1.25
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.0
        gateway 192.168.1.254
```

This might have something to do with my interfaces configuration although I doubt it because it didn't work before I configured anything.  All that matters is that I get connected to the internet.  Static or not doesn't matter at this point.

Thanks in advance for your time which will be greatly appreciated. :-)

---

### Post by DigitDuke on 2006-07-13
I might be realeasing a bit too much info, but this info from my router might also be of some help perhaps.

[FONT="Courier New"]Netopia Model 3347W Wireless DSL Ethernet Switch
Running Netopia SOC OS version 7.4.2 (build r4)
Multimode ADSL Capable
(Admin completed login: Full Read/Write access)
Serial number 11886040, CPU ARM940T, Product ID 1225
System Log Message counts:
  Low 0, Medium 0, High 54, Alerts 14, Lost 0, Total 68
Uptime 00:00:33:31
Date 7/13/06 10:19:50 PM
Available features:
Feature                    Mode       Expiration                    Notes
-------------------------- ---------- ----------------------------- ------------
Security Monitoring        Disabled                                 
ATM VCCs                   Keyed      None                          Limit: 1
PPPoE Sessions             Keyed      None                          Limit: 1
Concurrent WAN Users       Keyed      None                          Unlimited
Basic Firewall             Disabled                                 
VPN                        Disabled                                 
Enterprise Class Upgrade   Disabled                                 
Hotspot Support            Disabled                                 
Hotspot ExAuth Support     Disabled                                 
Hotspot Splash Support     Disabled                                 
Memory status:
Heap: total bytes 1747504 (free 711728, allocated 1035776)
System Packet Buffers: total 192 free 127 min 105
Image usage: text 2949948, data 672384, bss 774522
Ethernet driver statistics - 10/100 Ethernet
Type: 100BASET  Duplex: Full
Port Status:  Link up 
General:
 Transmit OK           : 2316
 Receive OK            : 169
 Tx Errors             : 0
 Rx Errors             : 0
 Rx CRC Errors         : 0
 Rx Frame Errors       : 0
Upper Layers:
 Rx No Handler         : 0
 Rx No Message         : 0
 Rx Octets             : 19082
 Rx Unicast Pkts       : 142
 Rx Multicast Pkts     : 0
 Tx Discards           : 0
 Tx Octets             : 171132
 Tx Unicast Pkts       : 207
 Tx Multicast Pkts     : 2109
Ethernet driver statistics - Wireless
Port Status:  Link up 
General:
 Transmit OK           : 5255
 Receive OK            : 4154
 Tx Errors             : 0
 Rx Errors             : 0
 Tx Octets             : 1796833
 Rx Octets             : 527014
ADSL Line State:        Up
ADSL Startup Attempts:  1
ADSL Modulation:        DMT
Datapump Version:       3.47
                        Downstream  Upstream
                        ----------  ----------
SNR Margin:                  22.17       15.00 dB
Line Attenuation:            39.37       17.00 dB
Output Power:                11.73       12.33 dB
Errored Seconds:                 0           0
Loss of Signal:                  0           0
Loss of Frame:                   0           0
CRC Errors:                      0           0
Data Rate:                    2304         576
ATM port status    : Up
Rx data rate (bps) : 2304
Tx data rate (bps) : 576
ATM Virtual Circuits:

VCC #  Type  VPI   VCI   Encapsulation
-----  ----  ---  -----  --------------------------
  1     PVC    8     48  PPP over ATM (VC-muxed)

ATM Circuit Statistics: VCC-8

  Rx Frames     :       2554           Tx Frames     :       2449
  Rx Octets     :    1527311           Tx Octets     :     274839
  Rx Errors     :          0           Tx Errors     :          0
  Rx Discards   :          0           Tx Discards   :          0
Wireless Statistics
  Wireless Protocol: 	IEEE 802.11b
  Wireless MAC Addr: 	00-00-c5-b5-5d-d8
  Network ID (SSID):	Brondukvisl 5  (Open System)
  Operating Channel:	7
  WPA-PSK Privacy Enabled
  Transmit OK           : 5255
  Receive OK            : 4154
  Tx Errors             : 0
  Rx Errors             : 0
IP interfaces:
Ethernet 100BT: ( up broadcast default rip-send v1 rip-receive v1 )
  inet 192.168.1.254 netmask 255.255.255.0 broadcast 192.168.1.255
  physical address 00-00-c5-b5-5d-d8 mtu 1500

PPP over ATM vcc1: ( up address-mapping broadcast default admin-disabled )
  inet 194.144.55.188 netmask 0.0.0.0 broadcast 255.255.255.255
  physical address 00-00-00-00-00-00 mtu 1500

IP Route Table:

Network Address-Mask------------via Router------Port------------------Type---
0.0.0.0/0.0.0.0                 217.151.181.57  WAN vcc1              Default

127.0.0.1/255.255.255.255       127.0.0.1       Loopback              Local

192.168.1.0/255.255.255.0       192.168.1.254   Ethernet 100BT        Local

192.168.1.254/255.255.255.255   192.168.1.254   Ethernet 100BT        Local

192.168.1.255/255.255.255.255   255.255.255.255 Ethernet 100BT        Bcast

224.0.0.0/224.0.0.0             0.0.0.0         --                    Other

224.0.0.9/255.255.255.255       0.0.0.0         --                    Other

239.255.255.250/255.255.255.255 0.0.0.0         --                    Other

255.255.255.255/255.255.255.255 255.255.255.255 --                    Bcast

Ethernet IP ARP table:
0: IP 192.168.1.25 Hardware 00-50-da-2d-ee-e4 flags VALID FIXED 
1: IP 192.168.1.5 Hardware 00-16-cb-06-32-f5 flags VALID 
2: IP 192.168.1.6 Hardware 00-03-47-ce-90-83 flags VALID 
3: IP 192.168.1.8 Hardware 00-11-25-a3-06-e4 flags VALID 
No firewall-related features are enabled. 

You may be able to extend the features of your Gateway by purchasing an Upgrade Key. A list of upgrades is available online at [http://www.netopia.com/en-us/equipment/purchase/cayman_sw_order.html](http://www.netopia.com/en-us/equipment/purchase/cayman_sw_order.html). To purchase an upgrade you must provide your serial number, which is: 11886040
IP NAT used list, total = 0
Key Inside_Address :Port     Outside_Address:Port     OPort  Life   Prot
No Bridge Interfaces:  bridge is disabled.
No Bridge table:  bridge is disabled.
The number of WAN users is unlimited.
When the number of WAN users is unlimited, this information
is not available.
DHCP: No Lease for client on interface WAN 1
DHCP server lease table:
Host Name          IP Address       Hardware Address  Status     Timeout  
                                                                 (dd:hh:mm:ss)
Thunderbolts       192.168.1.5      00-16-cb-06-32-f5 Active     00:00:54:23
IBM1               192.168.1.6      00-03-47-ce-90-83 Active     00:00:41:05
IBM2               192.168.1.8      00-11-25-a3-06-e4 Active     00:00:48:56
PPP driver information:
PPP: (WAN 1)
  NCP Protocol: (c021) LCP
  NCP state: OPEN

  LCP Options:
   Local MRU:  1500                      Remote MRU:     0
   Local to Peer ACC map: 0x00000000     Peer to Local ACC map: 0x00000000
   Local authentication type:  NONE      Remote authentication type:  CHAP
   Local magic number: 0x37350000        Remote magic number: 0x4da39861
   Transmit FCS size (in bits):  16      Receive FCS size (in bits):  16
   Local to Remote protocol compression: Disabled
   Remote to Local protocol compression: Disabled
   Local to Remote header and address compression: Disabled
   Remote to Local header and address compression: Disabled

  Packets in:          307        Packets Out:             0
  NCP Protocol: (8021) IPCP
  NCP state: OPEN

  IP Information:
   IP operation status: OPEN
   IP local to remote compression protocol: NONE
   IP remote to local compression protocol: NONE
  Packets in:         2238        Packets Out:          2130
No PPPoE sessions are currently active.
Crash of Netopia-3000/11886040 (Netopia-3000, rev 1), PID 1225, Model 3347W
running version 7.4.2r4

CPU was in Supervisor mode when crash occurred.  In Abort mode now.

Crash PC       : 0x85ffed
Frame Pointers:
 00821533
 0083d64d
 008b856c
 008baf14
Registers:
  R0     = 00d208fc  R1     = 000001b0  R2     = 6d782065  R3     = 0085fff9
  R4     = 000001c0  R5     = 001d87c9  R6     = 001d87c9  R7     = 001d872b
  R8     = c08193c3  R9     = 00000000  R10    = 00ce86c6  R11    = 00000000
  PC     = 0085fff4  CPSR   = 20000097  SPSR   = 20000033  R12    = 0085ff87
  SP_SVR = 00ce9628  SP_ABT = 00dbc800  SP_UND = fdbde24a  SP_IRQ = 008005f8
  LR_SVR = 0085fff9  LR_ABT = 0085fff4  LR_UND = acf5a3cf  LR_IRQ = 008b3cf8
  SP_FIQ = 008001fc  LR_FIQ = f27ffffa
Message Log:
00:00:00:00 L5      KS: Using configured options found in flash
00:00:00:00 L5      KS: Customer default options found in flash - using
00:00:00:00 L3      BOOT: Warm start v7.4.2 ---------------------------------- 
00:00:00:00 L3      IP address server initialization complete 
00:00:00:00 L4      BR: Using saved configuration options
00:00:00:00 L4      BR: Netopia SOC OS version 7.4.2 (build r4)
00:00:00:00 L4      BR: Netopia-3000/11886040 (Netopia-3000, rev 1), PID 1225
00:00:00:00 L4      BR: last install status: Firmware Update Was Successful
00:00:00:00 L4      BR: memory sizes - 2048K Flash, 8192K RAM
00:00:00:00 L3      BR: Starting kernel
00:00:00:00 L3      AAL5: initializing service
00:00:00:00 L4      ATM: Waiting for PHY layer to come up
00:00:00:00 L3      BRDG: Configuring port (10/100BT-LAN)
00:00:00:00 L3      BRDG: Bridge not enabled for WAN.
00:00:00:00 L3      BRDG: Bridging from one WAN port to another is disabled
00:00:00:00 L3      BRDG: Initialization complete
00:00:00:00 L4      IP: Routing between WAN ports is disabled
00:00:00:00 L4      IP: IPSec client pass through is enabled
00:00:00:00 L4      IP: Address mapping enabled on interface PPP over ATM vcc1
00:00:00:00 L3      IP: Adding default gateway over PPP over ATM vcc1
00:00:00:00 L3      IP: Initialization complete
00:00:00:00 L3      IPSec: initializing service
00:00:00:00 L3      IPSec: No feature key available - service disabled
00:00:00:00 L3      PPP: PPP over ATM vcc1 binding to PPPoA
00:00:00:00 L3      PPP: PPP over ATM vcc1 Port listening for incoming PPP connection requests
00:00:00:00 L3      BRDG: (10/100BT-LAN) Port Physical Link Active
00:00:00:00 L3      IP: (10/100BT-LAN) Ethernet Physical Link Active
00:00:00:00 L3      IP: (10/100BT-LAN) IP Protocol Up
00:00:00:00 L3      RIP: initializing
00:00:00:00 L3      DHCP: Initializing Service
00:00:00:00 L3      DHCP: Setup Server On UDP Port 67
00:00:00:00 L3      DHCP: Setup Client On UDP Port 68
00:00:00:00 L3      DNS: initializing service
00:00:00:00 L4      DNS: nameserver address is 0.0.0.0
00:00:00:00 L3      SNMP: initializing service over UDP
00:00:00:00 L3      DIA: Diagnostics service initializing
00:00:00:00 L3      FW: initializing service
00:00:00:00 L3      FW: Firewall service is disabled
00:00:00:00 L3      HB: heartbeat service initializing
00:00:00:00 L3      HB: heartbeat option disabled
00:00:00:00 L3      UPnP: Initialization complete
00:00:00:33 L3      lcp: LCP Send Config-Request+
00:00:00:35 L3      lcp: LCP Recv Config-Req:+
00:00:00:35 L4      lcp: ** Server wants authentication (PAP). Not configured for PAP.
00:00:00:35 L3       AUTHTYPE(c023) (PAP) (NAK) MAGICNUMBER(4da39861) (ACK)
00:00:00:35 L3      lcp: returning Configure-Nak
00:00:00:35 L3      lcp: LCP Recv Config-Req:+
00:00:00:35 L3       AUTHTYPE(c223) (CHAP) (ACK) MAGICNUMBER(4da39861) (ACK)
00:00:00:35 L3      lcp: returning Configure-Ack
00:00:00:35 L3      lcp: LCP Send Config-Request+
00:00:00:35 L3      chap: received challenge, id 1
00:00:00:35 L3      chap: received success, id 1
00:00:00:35 L3      ipcp: IPCP Config-Request+
00:00:00:35 L3       ADDR(0x0) DNS(0x0) DNS2(0x0) WINS(0x0) WINS2(0x0)
00:00:00:35 L3      ipcp: IPCP Recv Config-Req:+
00:00:00:35 L3       ADDR(217.151.181.57) (ACK)
00:00:00:35 L3      ipcp: returning Configure-ACK
00:00:00:35 L3      ipcp: IPCP Config-Request+
00:00:00:35 L3       ADDR(0x0) DNS(0x0) DNS2(0x0)
00:00:00:35 L3      ipcp: IPCP Config-Request+
00:00:00:35 L3       ADDR(0xc29037bc) DNS(0xc104c202) DNS2(0xd5b08033)
00:00:00:35 L3      ipcp: negotiated remote IP address 217.151.181.57
00:00:00:35 L3      ipcp: negotiated IP address 194.144.55.188
00:00:00:35 L3      ipcp: negotiated TCP hdr commpression off
00:00:00:36 L3      NTP: Update system date & time 
7/13/06 09:47:12 PM L4      HTTP: "Admin" completed login from 192.168.1.5
7/13/06 09:55:25 PM L4      HTTP: "Admin" host 192.168.1.5 logging out (timing out)
7/13/06 10:14:32 PM L4      HTTP: "Admin" completed login from 192.168.1.5[/FONT]

---

### Post by DigitDuke on 2006-07-14
Also, here is the output of my Mac's [FONT="Courier New"]ifconfig[/FONT] which has a working wireless connection on [FONT="Courier New"]en1[/FONT], IP [FONT="Courier New"]192.168.1.5[/FONT].

```
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
        inet6 ::1 prefixlen 128 
        inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
        inet 127.0.0.1 netmask 0xff000000 
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        ether 00:16:cb:8a:23:b7 
        media: autoselect status: inactive
        supported media: autoselect 10baseT/UTP <half-duplex> 10baseT/UTP <full-duplex> 10baseT/UTP <full-duplex,hw-loopback> 10baseT/UTP <full-duplex,flow-control> 100baseTX <half-duplex> 100baseTX <full-duplex> 100baseTX <full-duplex,hw-loopback> 100baseTX <full-duplex,flow-control> 1000baseT <full-duplex> 1000baseT <full-duplex,hw-loopback> 1000baseT <full-duplex,flow-control> none
en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        inet6 fe80::216:cbff:fe06:32f5%en1 prefixlen 64 scopeid 0x5 
        inet 192.168.1.5 netmask 0xffffff00 broadcast 192.168.1.255
        ether 00:16:cb:06:32:f5 
        media: autoselect status: active
        supported media: autoselect
wlt1: flags=41<UP,RUNNING> mtu 1500
vi2: flags=8963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1500
        inet6 fe80::201:23ff:fe45:6789%vi2 prefixlen 64 scopeid 0x7 
        inet 10.37.129.2 netmask 0xffffff00 broadcast 10.37.129.255
        ether 00:01:23:45:67:89 
        media: autoselect status: active
        supported media: autoselect
fw0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 494
        lladdr 00:16:cb:ff:fe:5a:e4:be 
        media: autoselect <full-duplex> status: inactive
        supported media: autoselect <full-duplex>
```

If there were to be some idiots out there they wouldn't even need to do the research before cracking me :P

---

### Post by DigitDuke on 2006-07-14
Hi there,

I've been searching the forums and similar threads for solutions but unfortunately I'm not finding anything that might work for my problem.

I'd really appreciate all suggestions and hints that might get me in the right direction.

Regards,
DigitDuke

---

### Post by G.Lindqvist on 2006-07-14
> **DigitDuke said:**
> Hi there,

I've been searching the forums and similar threads for solutions but unfortunately I'm not finding anything that might work for my problem.

I'd really appreciate all suggestions and hints that might get me in the right direction.

Regards,
DigitDuke

I got the same problem, isn't there any soultions for this problem?

---

### Post by DigitDuke on 2006-07-16
After a while of trying to figure this out, I figured out that it was my settings which were misconfigured.  All I did was change my /etc/network/interfaces file to:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

And then run
```
/etc/init.d/networking restart
```

---

### Post by morequarky on 2006-07-16
Your connected to your router by USB or Ethernet?

Ethernet?

Try 192.168.1.1 in a browser.  Can you edit your routers settings?  Does your router see your computer?

---

### Post by DigitDuke on 2006-07-16
I'm connecting via Ethernet.  I might not have said it clearly enough in the post above (or not at all it seems) but I've solved this problem by taking the steps enlisted above.

Thanks for taking the time of trying to help :-)

---

### Post by morequarky on 2006-07-16
Sorry, I saw your last post right after I posted. Sorry.

---

