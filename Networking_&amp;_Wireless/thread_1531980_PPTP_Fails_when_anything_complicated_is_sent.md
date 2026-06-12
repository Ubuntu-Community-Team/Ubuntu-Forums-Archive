---
title: "PPTP Fails when anything complicated is sent"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by StrangeWill on 2010-07-15
So I installed pptpd, got it configured and can connect and ping computers on my network, yay.

But when I try to hit my web server, remote desktop to my computer, or frankly anything but ping, the VPN connection goes down and the reconnect message appears.

Any ideas?


messages:
```


Jul 15 16:25:05 LinuxServer pppd[31564]: pppd 2.4.4 started by root, uid 0
Jul 15 16:25:05 LinuxServer pppd[31564]: Using interface ppp0
Jul 15 16:25:05 LinuxServer pppd[31564]: Connect: ppp0 <--> /dev/pts/0
Jul 15 16:25:09 LinuxServer pppd[31564]: MPPE 128-bit stateless compression enabled
Jul 15 16:25:11 LinuxServer pppd[31564]: found interface eth0 for proxy arp
Jul 15 16:25:11 LinuxServer pppd[31564]: local  IP address 192.168.10.10
Jul 15 16:25:11 LinuxServer pppd[31564]: remote IP address 192.168.10.240
Jul 15 16:25:13 LinuxServer pppd[31564]: Modem hangup
Jul 15 16:25:13 LinuxServer pppd[31564]: Connect time 0.1 minutes.
Jul 15 16:25:13 LinuxServer pppd[31564]: Sent 4472 bytes, received 3774 bytes.
Jul 15 16:25:13 LinuxServer pppd[31564]: Connection terminated.
Jul 15 16:25:14 LinuxServer pppd[31564]: Exit.

```

---

