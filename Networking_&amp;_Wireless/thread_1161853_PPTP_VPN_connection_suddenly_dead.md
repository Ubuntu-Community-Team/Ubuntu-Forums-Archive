---
title: "PPTP VPN connection suddenly dead"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by lajfi on 2009-05-17
hi,

i am running Ubuntu Jaunty on a sony vaio vgn-fz29vn.
in the office we have a firewall (netasq f25) and we are using pptp vpn in the firewall.
i can connect to the vpn, but after a while, the connection seems "inactive". i still have an IP on my office network, but i cant ping any of the servers any more.

i monitored my syslog while scp'ing some files, and at the exact moment where my connection was "lost", this is what was written in the log

```
May 17 10:28:06 ltp-leiv NetworkManager: <info>  Login Banner: 
May 17 10:28:06 ltp-leiv NetworkManager: <info>  ----------------------------------------- 
May 17 10:28:06 ltp-leiv NetworkManager: <info>  (null) 
May 17 10:28:06 ltp-leiv NetworkManager: <info>  ----------------------------------------- 
May 17 10:28:07 ltp-leiv NetworkManager: <info>  (ppp0): writing resolv.conf to /sbin/resolvconf 
May 17 10:28:07 ltp-leiv NetworkManager: <info>  VPN connection 'XXXX' (IP Config Get) complete. 
May 17 10:28:07 ltp-leiv NetworkManager: <info>  (ppp0): writing resolv.conf to /sbin/resolvconf 
May 17 10:28:07 ltp-leiv NetworkManager: <info>  Policy set 'XXXX' (ppp0) as default for routing and DNS. 
May 17 10:28:07 ltp-leiv NetworkManager: <info>  VPN plugin state changed: 4 
May 17 10:28:21 ltp-leiv bcrelay[1694]: UDP_BroadCast(sp=138,dp=138) from: wlan0 relayed to: 
^TMay 17 10:29:04 ltp-leiv pptp[4768]: nm-pptp-service-4746 log[logecho:pptp_ctrl.c:677]: Echo Request received.
May 17 10:29:04 ltp-leiv pptp[4768]: nm-pptp-service-4746 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply' 
May 17 10:29:49 ltp-leiv kernel: [  241.783832] mppe_decompress[0]: FLUSHED bit not set on flag packet!
May 17 10:29:49 ltp-leiv pppd[4752]: Protocol-Reject for unsupported protocol 'AppleTalk SmartBuffered' (0x3b)
May 17 10:29:50 ltp-leiv pppd[4752]: Protocol-Reject for unsupported protocol 0x6ad7
May 17 10:29:50 ltp-leiv pppd[4752]: Protocol-Reject for unsupported protocol 0x427b

```

so it seems it starts sending out PPP echo pakets, although i have disabled this in my VPN setup.

any thoughts on this anyone?

---

### Post by lajfi on 2009-05-21
i found out in the mean time that my DNS isn't working properly as well when connected to the vpn.
i didn't notice this before, since i had entered my hostnames in my hosts file and forgot about it....

otherwise, the problem still persists.....

---

### Post by pinoyskull on 2012-05-30
im going to revive thread instead of creating one, experienced this myself a while ago under Ubuntu 12.04

logs says

```
May 30 16:41:29 freedom pppd[7613]: Protocol-Reject for unsupported protocol 0x8d19
May 30 16:41:30 freedom pppd[7613]: Protocol-Reject for unsupported protocol 0xea72
May 30 16:41:30 freedom pppd[7613]: Protocol-Reject for unsupported protocol 0xf698
May 30 16:41:30 freedom pppd[7613]: Protocol-Reject for unsupported protocol 0x308b
May 30 16:41:30 freedom pppd[7613]: Protocol-Reject for unsupported protocol 0xc5eb
May 30 16:41:30 freedom pppd[7613]: Protocol-Reject for unsupported protocol 0xa4e8
May 30 16:41:31 freedom pppd[7613]: Protocol-Reject for unsupported protocol 0x9149
May 30 16:41:31 freedom pppd[7613]: Protocol-Reject for unsupported protocol 0xb4d0
May 30 16:41:31 freedom pppd[7613]: Protocol-Reject for unsupported protocol 0xb0e8
May 30 16:41:31 freedom pppd[7613]: Protocol-Reject for unsupported protocol 0xa38d

```

then after a while your PPTP VPN will cut off.

---

