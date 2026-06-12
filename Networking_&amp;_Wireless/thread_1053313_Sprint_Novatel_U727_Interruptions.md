---
title: "Sprint Novatel U727 Interruptions"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by robTard on 2009-01-28
Hi,

I have a Sprint Novatel U727 EVDO card.  It seems to connect, work for a bit, and then all of a sudden go down without warning for 10-15 seconds, and come back up with a new IP address causing a disruption in my service.

Here is the output from pppd debug after setting up pppd to log to /var/log/debug:
 1318 Jan 28 14:33:17 wings-laptop-4 pppd[7778]: using channel 4
   1319 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7e71be9c> <pcomp> <accomp>]
   1320 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: rcvd [LCP ConfReq id=0x48 <asyncmap 0x0> <magic 0x8e773d53> <pcomp> <accomp>]
   1321 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: sent [LCP ConfAck id=0x48 <asyncmap 0x0> <magic 0x8e773d53> <pcomp> <accomp>]
   1322 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x7e71be9c> <pcomp> <accomp>]
   1323 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: sent [LCP EchoReq id=0x0 magic=0x7e71be9c]
   1324 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
   1325 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
   1326 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: rcvd [LCP DiscReq id=0x49 magic=0x8e773d53]
   1327 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: rcvd [IPCP ConfReq id=0x65 <addr 68.28.145.69>]
   1328 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: sent [IPCP ConfAck id=0x65 <addr 68.28.145.69>]
   1329 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: rcvd [LCP EchoRep id=0x0 magic=0x8e773d53 7e 71 be 9c]
   1330 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: rcvd [LCP ProtRej id=0x4a 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
   1331 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
   1332 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
   1333 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
   1334 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: rcvd [IPCP ConfNak id=0x2 <addr 68.30.123.201> <ms-dns1 68.28.146.92> <ms-dns3 68.28.154.92>]
   1335 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: sent [IPCP ConfReq id=0x3 <addr 68.30.123.201> <ms-dns1 68.28.146.92> <ms-dns3 68.28.154.92>]
   1336 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: rcvd [IPCP ConfAck id=0x3 <addr 68.30.123.201> <ms-dns1 68.28.146.92> <ms-dns3 68.28.154.92>]
   1337 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: Script /etc/ppp/ip-up started (pid 7782)
   1338 Jan 28 14:33:19 wings-laptop-4 pppd[7778]: Script /etc/ppp/ip-up finished (pid 7782), status = 0x0
   1339 Jan 28 14:34:38 wings-laptop-4 pppd[7778]: rcvd [LCP TermReq id=0x4b]
   1340 Jan 28 14:34:38 wings-laptop-4 pppd[7778]: Script /etc/ppp/ip-down started (pid 8047)
   1341 Jan 28 14:34:38 wings-laptop-4 pppd[7778]: sent [LCP TermAck id=0x4b]
   1342 Jan 28 14:34:38 wings-laptop-4 pppd[7778]: Script /etc/ppp/ip-down finished (pid 8047), status = 0x0

It seems that I am getting an [LCP TermReq] and this seems to be
disconnecting me.

uname -a:
 2.6.24-21-eeepc #1 SMP Thu Aug 7 22:18:05 MDT 2008 i686 GNU/Linux

I am running an ASUS eeepc 900A.

Does anyone know what is going on ?  Is my card crashing and pppd is bringing it back up and in the process it is getting a new IP address from Sprint ?

---

