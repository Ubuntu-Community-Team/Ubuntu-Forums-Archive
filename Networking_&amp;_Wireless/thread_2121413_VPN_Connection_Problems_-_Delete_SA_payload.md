---
title: "VPN: Connection Problems - Delete SA payload"
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by dercommodore on 2013-03-01
Hey guys

I have the following problem:
I am desperately trying to set up a VPN (Openswan, XL2TP and PPP) connection for my iOS devices - but it doesn't work out.

I found this post in the Forum: [Guide: Openswan, XL2TP and PPP on Ubuntu Maverick for iPhone VPN Connection]("http://ubuntuforums.org/showthread.php?t=1645473"), which was already a great help.

Unfortunate it is still not working:
Here is my auth.log:

[PHP]
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: received Vendor ID payload [RFC 3947] method set to=109 
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike] method set to=110 
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: ignoring unknown Vendor ID payload [8f8d83826d246b6fc7a8a6a428c11de8]
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: ignoring unknown Vendor ID payload [439b59f8ba676c4c7737ae22eab8f582]
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: ignoring unknown Vendor ID payload [4d1e0e136deafa34c4f3ea9f02ec7285]
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: ignoring unknown Vendor ID payload [80d0bb3def54565ee84645d4c85ce3ee]
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: ignoring unknown Vendor ID payload [9909b64eed937c6573de52ace952fa6b]
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] meth=108, but already using method 110
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 110
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 110
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Mar  2 01:12:12 userver pluto[62850]: packet from 212.95.7.42:18153: received Vendor ID payload [Dead Peer Detection]
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[1] 212.95.7.42 #1: responding to Main Mode from unknown peer 212.95.7.42
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[1] 212.95.7.42 #1: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[1] 212.95.7.42 #1: STATE_MAIN_R1: sent MR1, expecting MI2
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[1] 212.95.7.42 #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): both are NATed
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[1] 212.95.7.42 #1: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[1] 212.95.7.42 #1: STATE_MAIN_R2: sent MR2, expecting MI3
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[1] 212.95.7.42 #1: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[1] 212.95.7.42 #1: Main mode peer ID is ID_IPV4_ADDR: '10.76.43.225'
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[1] 212.95.7.42 #1: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #1: deleting connection "L2TP-PSK-NAT" instance with peer 212.95.7.42 {isakmp=#0/ipsec=#0}
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #1: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #1: new NAT mapping for #1, was 212.95.7.42:18153, now 212.95.7.42:25955
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #1: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp1024}
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #1: Dead Peer Detection (RFC 3706): enabled
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #1: Applying workaround for Mac OS X NAT-OA bug, ignoring proposed subnet
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #1: the peer proposed: 93.83.192.138/32:17/1701 -> 212.95.7.42/32:17/0
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #2: responding to Quick Mode proposal {msgid:cec7f025}
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #2:     us: 192.168.1.3<192.168.1.3>[+S=C]:17/1701---192.168.1.2
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #2:   them: 212.95.7.42[10.76.43.225,+S=C]:17/52413
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #2: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #2: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #2: Dead Peer Detection (RFC 3706): enabled
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #2: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Mar  2 01:12:12 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #2: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x0215a7c2 <0xa5e673c7 xfrm=AES_256-HMAC_SHA1 NATOA=none NATD=212.95.7.42:25955 DPD=enabled}
Mar  2 01:12:32 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #1: received Delete SA(0x0215a7c2) payload: deleting IPSEC State #2
Mar  2 01:12:32 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #1: received and ignored informational message
Mar  2 01:12:32 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42 #1: received Delete SA payload: deleting ISAKMP State #1
Mar  2 01:12:32 userver pluto[62850]: "L2TP-PSK-NAT"[2] 212.95.7.42: deleting connection "L2TP-PSK-NAT" instance with peer 212.95.7.42 {isakmp=#0/ipsec=#0}
Mar  2 01:12:32 userver pluto[62850]: packet from 212.95.7.42:25955: received and ignored informational message
[/PHP]

What is the problem here? It seams to me the IPSEC connection is successfully build up but then it is somehow "lost" at 01:12:32 ...

Thanks for the help - I really appreciate it :KS

---

