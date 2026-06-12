---
title: "VPN PPTP with a server."
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by agkbill on 2010-01-24
Hi,

I am in the process of setting up a VPN connection using PPTP and had some success but I am now stuck.

I have a small linux server callled Bubba2 and connected to a UBUNTU PC and one SGI running IRIX.






Setup is like this.

Internet ---> Bubba2,Wan
Bubba2,Lan ----> router,Wan (router is a Netgear 3500L)

Then my two computers are connected to the router.

I have set up a NFS sharing to my bubba2 that works great, also ssh and everything works just fine.

What I whant now it for bubba2 to take care of my torrents, using VPN, PPTP connection.

The VPN is only a 20 Mbit, normal I get around 80-90 Mbit.

So I would like only the bittorrent to use my VPN tunnel.

Further if possible, my internet provider gives I think 3 or 4 IP using DHCP. Uppload capacity is spreed over the IP so it would be great if Bubba could be assigned with one IP and the rest with another.

But my main objective is to get the bubba torrent to use VPN, PPTP, and for the NFS, SSH to bubba to work like they do now.

Any suggestion on how I best accomplies this.


I managed to get the tunnel up and running.


---------------------------------------------------------------------------------------------------------------------------------------------------
bubba:/home/christer# ifconfig
eth0 Link encap:Ethernet HWaddr 00:22:02:00:0A:BE
inet addr:213.112.225.41 Bcast:213.112.239.255 Mask:255.255.240.0
inet6 addr: fe80::222:2ff:fe00:abe/64 Scope:Link
UP BROADCAST RUNNING MTU:1500 Metric:1
RX packets:455229999 errors:83 dropped:0 overruns:0 frame:5768
TX packets:647158971 errors:31793133 dropped:0 overruns:18659 carrier:31793133
collisions:9002243 txqueuelen:1000
RX bytes:4258887600 (3.9 GiB) TX bytes:1039860741 (991.6 MiB)
Base address:0xe000

eth1 Link encap:Ethernet HWaddr 00:22:02:00:0A:BF
inet addr:192.168.10.1 Bcast:192.168.10.255 Mask:255.255.255.0
inet6 addr: fe80::222:2ff:fe00:abf/64 Scope:Link
UP BROADCAST RUNNING ALLMULTI MULTICAST MTU:1500 Metric:1
RX packets:646974855 errors:16 dropped:0 overruns:0 frame:0
TX packets:424625213 errors:0 dropped:0 overruns:448 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3445824051 (3.2 GiB) TX bytes:3328713731 (3.1 GiB)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:780 errors:0 dropped:0 overruns:0 frame:0
TX packets:780 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:77328 (75.5 KiB) TX bytes:77328 (75.5 KiB)

ppp0 Link encap:Point-to-Point Protocol
inet addr:93.182.150.142 P-t-P:93.182.150.2 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1496 Metric:1
RX packets:7 errors:0 dropped:0 overruns:0 frame:0
TX packets:36434 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3
RX bytes:239 (239.0 b) TX bytes:14739577 (14.0 MiB)

bubba:/home/christer#
---------------------------------------------------------------------------------------------------------------------------------------------

But after 2 min (maybe a timeout) it disconects.

Logg of the connection:

---------------------------------------------------------------------------------------------------------------------------------------------
bubba:/home/christer# pon CE debug dump logfd 2 nodetach
pppd options in effect:
debug # (from command line)
nodetach # (from command line)
logfd 2 # (from command line)
dump # (from command line)
noauth # (from /etc/ppp/options.pptp)
name ***** # (from /etc/ppp/peers/CE)
remotename IPRED # (from /etc/ppp/peers/CE)
# (from /etc/ppp/options.pptp)
pty pptp vpn.ipredator.se --nolaunchpppd # (from /etc/ppp/peers/CE)
crtscts # (from /etc/ppp/options)
# (from /etc/ppp/options)
asyncmap 0 # (from /etc/ppp/options)
lcp-echo-failure 4 # (from /etc/ppp/options)
lcp-echo-interval 30 # (from /etc/ppp/options)
hide-password # (from /etc/ppp/options)
ipparam CE # (from /etc/ppp/peers/CE)
proxyarp # (from /etc/ppp/options)
nobsdcomp # (from /etc/ppp/options.pptp)
nodeflate # (from /etc/ppp/options.pptp)
require-mppe-128 # (from /etc/ppp/peers/CE)
noipx # (from /etc/ppp/options)
using channel 41
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x973d7c38> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xaa6a6ace> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xaa6a6ace> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x973d7c38> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x973d7c38]
rcvd [LCP EchoReq id=0x0 magic=0xaa6a6ace]
sent [LCP EchoRep id=0x0 magic=0x973d7c38]
rcvd [CHAP Challenge id=0x8e <50fc0665f2f8fe976f13c1dccd7c6a46>, name = "pptpd"]
sent [CHAP Response id=0x8e <fdc0f65868b8b2f65d6d1f93c63447d50000000000000000963eab867b0d739935f1aacedb6f3f2b7d231607f9fb440500>, name = "*****"]
rcvd [LCP EchoRep id=0x0 magic=0xaa6a6ace]
rcvd [CHAP Success id=0x8e "S=9660C795E4A5E87B3CF4484EC9A8E631E4B6F62D"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 93.182.132.2>]
sent [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 93.182.132.2>]
rcvd [IPCP ConfNak id=0x1 <addr 93.182.132.104>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 93.182.132.104>]
rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 93.182.132.104>]
Cannot determine ethernet address for proxy ARP
local IP address 93.182.132.104
remote IP address 93.182.132.2
Script /etc/ppp/ip-up started (pid 8511)
Script /etc/ppp/ip-up finished (pid 8511), status = 0x0
Modem hangup
Connect time 2.1 minutes.
Sent 92488211 bytes, received 1695 bytes.
Script /etc/ppp/ip-down started (pid 8544)
MPPE disabled
sent [LCP TermReq id=0x2 "MPPE disabled"]
Connection terminated.
Script pptp vpn.ipredator.se --nolaunchpppd finished (pid 8504), status = 0x0
Waiting for 1 child processes...
script /etc/ppp/ip-down, pid 8544
Script /etc/ppp/ip-down finished (pid 8544), status = 0x0
bubba:/home/christer#

---------------------------------------------------------------------------------------------------------------------------------------

Maybe something is not correct with my routing, I have not changed anything from original bubba2 settings.

it looks like:

-----------------------------------------------------------------------------------------------------------------------------------------
bubba:/home/christer# route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.10.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
213.112.224.0 0.0.0.0 255.255.240.0 U 0 0 0 eth0
239.0.0.0 0.0.0.0 255.0.0.0 U 0 0 0 eth1
0.0.0.0 213.112.224.1 0.0.0.0 UG 0 0 0 eth0
bubba:/home/christer#
---------------------------------------------------------------------------------------------------------------------------------------



Any ideas on how to accomplish this?

All suggestion mostly appreciated.


Best regards,

/Christer

---

