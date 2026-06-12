---
title: "USB modem PDP context activation faile"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by janl8x8 on 2011-01-06
Hi everybody,
I have wyless USB modem. It works under Win 7, but in Ubuntu does not. After sudo wvdial:
Jan  6 16:58:17 ubuntu pppd[8705]: Connect: ppp0 <--> /dev/ttyACM0
Jan  6 16:58:17 ubuntu pppd[8705]: Remote message: Login OK
Jan  6 16:58:17 ubuntu pppd[8705]: PAP authentication succeeded
Jan  6 16:58:18 ubuntu pppd[8705]: LCP terminated by peer (PDP context activation failed, no network protocol running)
in log:
Jan  6 16:59:51 ubuntu pppd[8720]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x5a2db03d> <pcomp> <accomp>]
Jan  6 16:59:51 ubuntu pppd[8720]: rcvd [LCP ConfReq id=0x1 <asyncmap 0xa0000> <auth pap>]
Jan  6 16:59:51 ubuntu pppd[8720]: sent [LCP ConfAck id=0x1 <asyncmap 0xa0000> <auth pap>]
Jan  6 16:59:51 ubuntu pppd[8720]: rcvd [LCP ConfRej id=0x1 <magic 0x5a2db03d> <pcomp> <accomp>]
Jan  6 16:59:51 ubuntu pppd[8720]: sent [LCP ConfReq id=0x2 <asyncmap 0x0>]
Jan  6 16:59:51 ubuntu pppd[8720]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0>]
Jan  6 16:59:51 ubuntu pppd[8720]: sent [LCP EchoReq id=0x0 magic=0x0]
Jan  6 16:59:51 ubuntu pppd[8720]: sent [PAP AuthReq id=0x1 user="7" password=<hidden>]
Jan  6 16:59:51 ubuntu pppd[8720]: rcvd [LCP EchoRep id=0x0 magic=0x0]
Jan  6 16:59:51 ubuntu pppd[8720]: rcvd [PAP AuthAck id=0x1 "Login OK"]
Jan  6 16:59:51 ubuntu pppd[8720]: Remote message: Login OK
Jan  6 16:59:51 ubuntu pppd[8720]: PAP authentication succeeded
Jan  6 16:59:51 ubuntu pppd[8720]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Jan  6 16:59:52 ubuntu pppd[8720]: rcvd [LCP TermReq id=0x2 "PDP context activation failed, no network protocol running"]
Jan  6 16:59:52 ubuntu pppd[8720]: LCP terminated by peer (PDP context activation failed, no network protocol running)
Jan  6 16:59:52 ubuntu pppd[8720]: sent [LCP TermAck id=0x2]

How can I "start network". I am grennie with Linux. Thank for any help,
Jan

---

### Post by janl8x8 on 2011-01-07
Pardon. Older version of Ubuntu. Now it works perfectly.

---

