---
title: "PPP VPN chap MS-v2"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by pwpeterson on 2009-08-20
I just set up a new Ubuntu 9.04 VPS, installed network-manager-pptp and  followed the instruction I found here to configure the connection: [http://pptpclient.sourceforge.net/howto-ubuntu.phtml#configure_by_hand](http://pptpclient.sourceforge.net/howto-ubuntu.phtml#configure_by_hand)  

After I start the connection using: 'pon vpn_xxx debug logfd 2 nodetach' a connection is made but appears to have problems authenticating.

I did some searching and tried a few things but none resolved the problem.

I suspect it maybe the vpn server I am trying to connect to is using 'chap MS-v2'.

How do I enable 'chap MS-v2' with my ppp client?

Below is a syslog extract from a recent attempt:

   Aug 20 15:47:29 c1422 pppd[22355]: pppd 2.4.5 started by root, uid 0
  Aug 20 15:47:29 c1422 pptp[22358]: anon log[main ptp.c:314]: The synchronous pptp option is NOT activated
  Aug 20 15:47:29 c1422 pppd[22355]: using channel 22
  Aug 20 15:47:29 c1422 pppd[22355]: Using interface ppp0
  Aug 20 15:47:29 c1422 pppd[22355]: Connect: ppp0 <--> /dev/pts/3
  Aug 20 15:47:29 c1422 pptp[22368]: anon log[ctrlp_rep ptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
  Aug 20 15:47:29 c1422 pptp[22368]: anon log[ctrlp_disp ptp_ctrl.c:739]: Received Start Control Connection Reply
  Aug 20 15:47:29 c1422 pptp[22368]: anon log[ctrlp_disp ptp_ctrl.c:773]: Client connection established.
  Aug 20 15:47:30 c1422 pppd[22355]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xc3d96311> <pcomp> <accomp>]
  Aug 20 15:47:30 c1422 pptp[22368]: anon log[ctrlp_rep ptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
  Aug 20 15:47:30 c1422 pptp[22368]: anon log[ctrlp_disp ptp_ctrl.c:858]: Received Outgoing Call Reply.
  Aug 20 15:47:30 c1422 pptp[22368]: anon log[ctrlp_disp ptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 26802).
  Aug 20 15:47:30 c1422 pppd[22355]: rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MS-v2> <magic 0x637c9441> <pcomp> <accomp>]
  Aug 20 15:47:30 c1422 pppd[22355]: No auth is possible
  Aug 20 15:47:30 c1422 pppd[22355]: sent [LCP ConfRej id=0x1 <auth chap MS-v2>]
  Aug 20 15:47:30 c1422 pppd[22355]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xc3d96311> <pcomp> <accomp>]
  Aug 20 15:47:30 c1422 pppd[22355]: rcvd [LCP ConfReq id=0x2 <asyncmap 0x0> <auth chap MS> <magic 0x637c9441> <pcomp> <accomp>]
  Aug 20 15:47:30 c1422 pppd[22355]: No auth is possible
  Aug 20 15:47:30 c1422 pppd[22355]: sent [LCP ConfRej id=0x2 <auth chap MS>]
  Aug 20 15:47:30 c1422 pppd[22355]: rcvd [LCP ConfReq id=0x3 <asyncmap 0x0> <auth chap MD5> <magic 0x637c9441> <pcomp> <accomp>]
  Aug 20 15:47:30 c1422 pppd[22355]: No auth is possible
  Aug 20 15:47:30 c1422 pppd[22355]: sent [LCP ConfRej id=0x3 <auth chap MD5>]
  Aug 20 15:47:30 c1422 pppd[22355]: rcvd [LCP ConfReq id=0x4 <asyncmap 0x0> <magic 0x637c9441> <pcomp> <accomp>]
  Aug 20 15:47:30 c1422 pppd[22355]: sent [LCP ConfAck id=0x4 <asyncmap 0x0> <magic 0x637c9441> <pcomp> <accomp>]
  Aug 20 15:47:30 c1422 pppd[22355]: sent [LCP EchoReq id=0x0 magic=0xc3d96311]
  Aug 20 15:47:30 c1422 pppd[22355]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 74.112.169.7>]
  Aug 20 15:47:30 c1422 pppd[22355]: rcvd [LCP TermReq id=0x5 "peer refused to authenticate"]
  Aug 20 15:47:30 c1422 pppd[22355]: LCP terminated by peer (peer refused to authenticate)
  Aug 20 15:47:30 c1422 pppd[22355]: sent [LCP TermAck id=0x5]
  Aug 20 15:47:30 c1422 pptp[22368]: anon log[pptp_read_some ptp_ctrl.c:544]: read returned zero, peer has closed
  Aug 20 15:47:30 c1422 pptp[22368]: anon log[callmgr_main ptp_callmgr.c:258]: Closing connection (shutdown)
  Aug 20 15:47:30 c1422 pptp[22368]: anon log[ctrlp_rep ptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
  Aug 20 15:47:30 c1422 pptp[22368]: anon log[pptp_read_some ptp_ctrl.c:544]: read returned zero, peer has closed
  Aug 20 15:47:30 c1422 pptp[22368]: anon log[call_callback ptp_callmgr.c:79]: Closing connection (call state)
  Aug 20 15:47:30 c1422 pppd[22355]: Script pptp 74.42.17.146 --nolaunchpppd finished (pid 22357), status = 0x0
  Aug 20 15:47:30 c1422 pppd[22355]: Modem hangup
  Aug 20 15:47:30 c1422 pppd[22355]: Connection terminated.
  Aug 20 15:47:30 c1422 pppd[22355]: Exit.
  
Any help would be greatly appreciated.
pwp

---

### Post by pwpeterson on 2009-08-21
Current options file settings:

asyncmap 0
auth
crtscts
local
lock
hide-password
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

pwp

---

### Post by pwpeterson on 2009-08-22
Any ideas, anyone?

---

### Post by pwpeterson on 2009-08-22
The solution was to put the username in quotes in the chap-secrets file.

---

