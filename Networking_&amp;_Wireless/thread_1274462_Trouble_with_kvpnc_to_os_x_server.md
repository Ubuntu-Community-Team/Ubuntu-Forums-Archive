---
title: "Trouble with kvpnc to os x server"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by mihaisofti on 2009-09-24
I'm trying to connect from my ubuntu 804 by vpn to my work server which is os x leopard server.  I'm using kvpnc and have configured it to connect using pptp.  it goes through the motions, and the leopard server responds, but then disconnects, and this is part of the log entry:

Thu Sep 24 17:57:08 2009 : lcp_reqci: returning CONFACK.
Thu Sep 24 17:57:08 2009 : sent [LCP ConfAck id=0x1 <mru 1492> <asyncmap 0x0> <magic 0xe83449e3> <pcomp> <accomp>]
Thu Sep 24 17:57:08 2009 : sent [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0xdb4e1247> <pcomp> <accomp>]
Thu Sep 24 17:57:11 2009 : PPTP received Call Clear Request message
Thu Sep 24 17:57:11 2009 : PPTP hangup
Thu Sep 24 17:57:11 2009 : Connection terminated.
Thu Sep 24 17:57:11 2009 : PPTP disconnecting...
Thu Sep 24 17:57:11 2009 : PPTP disconnected
2009-09-24 17:57:11 BST   --> Client with address = 192.168.1.28 has hungup

The log from kvpnc is as follows:

debug: Connect try requested, profile: TTL_PPTP_1, type: PPTP
debug: pppd: /usr/sbin/pppd
debug: /usr/sbin/pppd has MPPE support and uses new style.
debug: Test support of replacedefaultroute pppd: failed
debug: Test support of require MPPE 128 pppd: failed
debug: No default interface given, tried default interface, got success, using "eth0".
debug: pppd peer script: /etc/ppp/peers/kvpnc.TTL_PPTP_1 
debug: Authentication method: chap
debug: pppd secrets file: /etc/ppp/chap-secrets
debug: Username: *********
debug: chmod of /etc/ppp/chap-secrets (go-rwx) started.
debug: pppd: /usr/sbin/pppd 
debug: Trying to connect to server "xxx.xxx.xxx.xxx" with user "*********"... 
debug: Setting DNS_UPDATE "Yes".
debug: "pppd" started.
debug: [pppd] using channel 19
debug: [pppd] Using interface ppp0
debug: [pppd] Connect: ppp0 /dev/pts/0
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] LCP: timeout sending Config-Requests
debug: [pppd] Connection terminated.
info: Connection has been terminated.
debug: There is a reason for stop connecting, terminating "pppd" process.
debug: pppd secrets file: /etc/ppp/chap-secrets
debug: [pppd] Modem hangup
error: Remote modem has hung up. Connection was terminated.
debug: There is a reason for stop connecting, terminating "pppd" process.
debug: pppd secrets file: /etc/ppp/chap-secrets

It seems that I'm almost there, but something is going wrong.  I get the mppe failure message whether I check the box or not.
Any help would be greatly appreciated

---

### Post by mihaisofti on 2009-09-25
Perhaps that was a heavy first post in a thread. I'm trying to connect from Ubuntu 8.04 to a Macintosh Leopard server over vpn. I've connected easily from a wireless mac laptop, but I'm unable to connect using native linux vpn, kvpnc, command line vpn using either l2tp or pptp of any flavour.

Who's got a quick fix?

---

### Post by mihaisofti on 2009-09-25
Or a non-assuming slow fix?

---

### Post by mihaisofti on 2009-09-25
I have the logs, for anyone who might understand them. From both ends and from Wireshark (Ethereal as was).

---

