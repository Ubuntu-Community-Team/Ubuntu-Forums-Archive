---
title: "ZTE MF192 3G modem with Orange.ug"
date: 2012-06-30
forum: Networking &amp; Wireless
---

### Post by redxine on 2012-06-30
I picked up a 3G dongle from Orange, a local Ugandan telco.  After getting modeswitching working, I can work with the modem fine on /dev/ttyACM0, but network manager refused to connect.

After installing KPPP and trying to get things up and running manually, the log reveals this little gem:
```
Jun 30 12:26:47 redxine-laptop pppd[4307]: rcvd [LCP EchoRep id=0x0 magic=0x178634ae]
Jun 30 12:26:47 redxine-laptop pppd[4307]: rcvd [PAP AuthAck id=0x1 "Icera PPP - Password Verified OK"]
Jun 30 12:26:47 redxine-laptop pppd[4307]: Remote message: Icera PPP - Password Verified OK
Jun 30 12:26:47 redxine-laptop pppd[4307]: PAP authentication succeeded
Jun 30 12:26:47 redxine-laptop pppd[4307]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jun 30 12:26:49 redxine-laptop pppd[4307]: rcvd [LCP TermReq id=0x0 "0021: Normal Termination by NCP"]
Jun 30 12:26:49 redxine-laptop pppd[4307]: LCP terminated by peer (0021: Normal Termination by NCP)
Jun 30 12:26:49 redxine-laptop pppd[4307]: sent [LCP TermAck id=0x0]
Jun 30 12:26:49 redxine-laptop pppd[4307]: Hangup (SIGHUP)
Jun 30 12:26:49 redxine-laptop pppd[4307]: Modem hangup
Jun 30 12:26:49 redxine-laptop pppd[4307]: Connection terminated.
Jun 30 12:26:49 redxine-laptop pppd[4307]: Exit.
```

I had to add the noccp flag in pppd to get the connection to go this far, but no matter what I do as soon as I try to request an IP the modem hangs up.  Has anyone gotten these working?

---

