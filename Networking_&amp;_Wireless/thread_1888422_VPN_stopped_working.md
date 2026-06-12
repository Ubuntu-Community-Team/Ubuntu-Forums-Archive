---
title: "VPN stopped working"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by Firapora on 2011-11-29
I inherited a VPN that's running on Ubuntu 10.04.3 server. The server itself has a dynamic IP, so in the past I connected via a URL at dyndns.org. It uses L2TP/PPP(Microsoft CHAP Version 2) - but aside from that I don't have much information about it.

Unfortunately it seems I am no longer able to connect to it remotely. I can still connect to it from inside the company network via SSH.

The remote machine I'm currently trying to connect from is a 10.04 client, though I wasn't able to get it to work on a Mac or Windows machine either, so I guess it's not a problem with the client setup. I'm using l2tp-ipsec-vpn from the ppa:werner-jaeger/ppa-werner-vpn repository. After setting up a connection with it, I tried to connect to the VPN (which fails). 

The log output of the connection attempt is posted below. Any help in getting issue fixed would be appreciated.

ipsec_setup: Stopping Openswan IPsec...
Stopping xl2tpd: xl2tpd.
xl2tpd[2458]: death_handler: Fatal signal 15 received
ipsec_setup: Starting Openswan IPsec U2.6.31/K2.6.32-35-generic...
Nov 29 20:43:29 lego ipsec__plutorun: Starting Pluto subsystem...
Nov 29 20:43:29 lego ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
recvref[22]: Protocol not available
xl2tpd[3779]: This binary does not support kernel L2TP.
Starting xl2tpd: xl2tpd.
xl2tpd[3780]: xl2tpd version xl2tpd-1.2.5 started on lego PID:3780
xl2tpd[3780]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
xl2tpd[3780]: Forked by Scott Balmos and David Stipp, (C) 2001
xl2tpd[3780]: Inherited by Jeff McAdams, (C) 2002
xl2tpd[3780]: Forked again by Xelerance ([www.xelerance.com](www.xelerance.com)) (C) 2006
xl2tpd[3780]: Listening on IP address 0.0.0.0, port 1701
Nov 29 20:43:30 lego ipsec__plutorun: 002 added connection description "XXX"
Nov 29 20:43:30 lego ipsec__plutorun: 003 NAT-Traversal: Trying new style NAT-T
Nov 29 20:43:30 lego ipsec__plutorun: 003 NAT-Traversal: ESPINUDP(1) setup failed for new style NAT-T family IPv4 (errno=19)
Nov 29 20:43:30 lego ipsec__plutorun: 003 NAT-Traversal: Trying old style NAT-T
104 "XXX" #1: STATE_MAIN_I1: initiate
003 "XXX" #1: received Vendor ID payload [Openswan (this version) 2.6.31 ]
003 "XXX" #1: received Vendor ID payload [Dead Peer Detection]
003 "XXX" #1: received Vendor ID payload [RFC 3947] method set to=109 
106 "XXX" #1: STATE_MAIN_I2: sent MI2, expecting MR2
003 "XXX" #1: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): both are NATed
108 "XXX" #1: STATE_MAIN_I3: sent MI3, expecting MR3
003 "XXX" #1: received Vendor ID payload [CAN-IKEv2]
004 "XXX" #1: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_128 prf=oakley_sha group=modp2048}
117 "XXX" #2: STATE_QUICK_I1: initiate
004 "XXX" #2: STATE_QUICK_I2: sent QI2, IPsec SA established transport mode {ESP=>0x781302b8 <0x0d3782ea xfrm=AES_128-HMAC_SHA1 NATOA=none NATD=XXX.XXX.XXX.XXX:4500 DPD=none}
xl2tpd[3780]: Connecting to host XXXX.dyndns.org, port 1701
xl2tpd[3780]: Connection established to XXX.XXX.XXX.XXX, 1701.  Local: 22224, Remote: 58304 (ref=0/0).
xl2tpd[3780]: Calling on tunnel 22224
xl2tpd[3780]: check_control: Received out of order control packet on tunnel 58304 (got 0, expected 1)
xl2tpd[3780]: handle_packet: bad control packet!
xl2tpd[3780]: check_control: Received out of order control packet on tunnel 58304 (got 0, expected 1)
xl2tpd[3780]: handle_packet: bad control packet!
xl2tpd[3780]: Call established with XXX.XXX.XXX.XXX, Local: 9096, Remote: 18022, Serial: 1 (ref=0/0)
xl2tpd[3780]: start_pppd: I'm running: 
xl2tpd[3780]: "/usr/sbin/pppd" 
xl2tpd[3780]: "passive" 
xl2tpd[3780]: "nodetach" 
xl2tpd[3780]: ":" 
xl2tpd[3780]: "file" 
xl2tpd[3780]: "/etc/ppp/XXX.options.xl2tpd" 
xl2tpd[3780]: "/dev/pts/0" 
pppd[3832]: Plugin passprompt.so loaded.
pppd[3832]: pppd 2.4.5 started by root, uid 0
pppd[3832]: Using interface ppp0
pppd[3832]: Connect: ppp0 <--> /dev/pts/0
xl2tpd[3780]: control_finish: Connection closed to XXX.XXX.XXX.XXX, serial 1 ()
xl2tpd[3780]: Terminating pppd: sending TERM signal to pid 3832
pppd[3832]: Terminating on signal 15
pppd[3832]: Modem hangup
pppd[3832]: Connection terminated.
pppd[3832]: Exit.
xl2tpd[3780]: pppd 3832 successfully terminated
Stopping xl2tpd: xl2tpd.
xl2tpd[3780]: death_handler: Fatal signal 15 received
ipsec_setup: Stopping Openswan IPsec...

---

### Post by Firapora on 2011-12-01
At this point it would already help if someone could tell me what exactly the log is saying about why it's supposedly not working.

I assume this is where the problem lies?
xl2tpd[3780]: check_control: Received out of order control packet on tunnel 58304 (got 0, expected 1)
xl2tpd[3780]: handle_packet: bad control packet!

Does it just mean that l2tp simply isn't working?

Alternatively any advice on how to go about finding out what VPN software it is that's actually running on the server would also be appreciated.

---

