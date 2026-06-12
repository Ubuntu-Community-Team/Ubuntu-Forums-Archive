---
title: "Connecting to VPN using l2tp"
date: 2006-05-22
forum: Networking &amp; Wireless
---

### Post by artik on 2006-05-22
Hello,
I need to connect to VPN network (not ISP) that uses l2tp access method.
I try to connect to VPN using IP, Username and password. The connection is not encrypted using PAP.

I'm running Ubuntu Breezy.

I've installed l2tpd, added following lines to /etc/l2tp/l2tpd.conf

[lac my-vpn]
lns = xx.yy.zz.tt

in /etc/ppp/pap-secrets I've added line with passwords and user name.

The connection fails on authentication: There is the log:
May 19 20:26:31 localhost pppd[17339]: sent [PAP AuthReq id=0x1 user="artyom-linux" password=<hidden>]
May 19 20:26:32 localhost pppd[17339]: rcvd [LCP EchoRep id=0x0 magic=0x23a3a15d]
May 19 20:26:34 localhost pppd[17339]: rcvd [PAP AuthNak id=0x1 "Request Denied"]
May 19 20:26:34 localhost pppd[17339]: Remote message: Request Denied
May 19 20:26:34 localhost pppd[17339]: PAP authentication failed

I must admit that "artyom-linux" is user field in the log is not the username I've set in pap-secrets.
I've tryed to add noauth to /etc/ppp/options - no results.

Can somebody tell me what have I done wrong?
Or maybe there is some good instrutions on connecting to VPN network from linux using l2tp?

Thanks!

---

