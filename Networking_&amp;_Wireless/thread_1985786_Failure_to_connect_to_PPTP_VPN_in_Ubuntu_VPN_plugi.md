---
title: "Failure to connect to PPTP VPN in Ubuntu: VPN plugin failed: 1"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by Banonran on 2012-05-23
I used network-manager-pptp under Ubuntu 12.04 to configure the vpn.

```
IPv4 Settings: 
Automatic

VPN: 
Gateway - set
User name - set
Password - Always Ask

PPTP Advanced Option:
PAP, CHAP, MSCHAP, EAP - unchecked
MSCHAPv2 - checked
Use Point-to Point encryption (MPPE) - checked
Securtity - 128-bit

all other settings are unchecked
```

But always I get the same message when I try to connect to the vpn: connection failed. The same issues was on the Ubuntu 10.04. In the sys log I have:
```
<info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 3042
May 23 22:17:42 NR5 NetworkManager[983]: <info> VPN service 'pptp' appeared; activating connections
May 23 22:17:42 NR5 NetworkManager[983]: <info> VPN plugin state changed: init (1)
May 23 22:17:42 NR5 NetworkManager[983]: <info> VPN plugin state changed: starting (3)
May 23 22:17:42 NR5 NetworkManager[983]: <info> VPN connection 'VPN NAME' (Connect) reply received.
May 24 00:21:00 NR5 pppd[9773]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
May 24 00:21:00 NR5 pppd[9773]: pppd 2.4.5 started by root, uid 0
May 24 00:21:00 NR5 pppd[9773]: Using interface ppp0
May 24 00:21:00 NR5 pppd[9773]: Connect: ppp0 <--> /dev/pts/3
May 24 00:21:00 NR5 pptp[9776]: nm-pptp-service-9764 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
May 23 22:17:42 NR5 NetworkManager[983]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 23 22:17:42 NR5 NetworkManager[983]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
May 24 00:21:01 NR5 pptp[9786]: nm-pptp-service-9764 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
May 24 00:21:01 NR5 pptp[9786]: nm-pptp-service-9764 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
May 24 00:21:01 NR5 pptp[9786]: nm-pptp-service-9764 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
May 24 00:21:02 NR5 pptp[9786]: nm-pptp-service-9764 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
May 24 00:21:02 NR5 pptp[9786]: nm-pptp-service-9764 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
May 24 00:21:02 NR5 pptp[9786]: nm-pptp-service-9764 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 32930).
May 24 00:21:31 NR5 pppd[9773]: LCP: timeout sending Config-Requests
May 24 00:21:31 NR5 pppd[9773]: Connection terminated.
May 23 22:18:13 NR5 NetworkManager[983]: <warn> VPN plugin failed: 1
May 23 22:18:14 NR5 NetworkManager[983]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
May 23 22:18:14 NR5 NetworkManager[983]: <warn> VPN plugin failed: 1
May 23 22:18:14 NR5 NetworkManager[983]: <warn> VPN plugin failed: 1
May 23 22:18:14 NR5 NetworkManager[983]: <info> VPN plugin state changed: stopped (6)
May 23 22:18:14 NR5 NetworkManager[983]: <info> VPN plugin state change reason: 0
May 23 22:18:14 NR5 NetworkManager[983]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
```

Before I started the vpn connection, the routing table looks:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
```

After I tried to start vpn, the ip-address X.X.X.X from the vpn server was added to the routing table:

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
X.X.X.X         192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
```

Also the same VPN-Connection works on the same machine under Windows without problem.

If you have some suggestions, I would be happy. Thank you a lot.

---

### Post by Banonran on 2012-05-23
I solved this problem. I created a virtual server (Port Forwarding) on my router for vpn: protocol TCP & GRE port 1723 and to my pc to the same port.

I did not think that the problem was on my router, because vpn connection works on the same pc under windows. But I found this [post]("http://vpnblog.info/ubuntu-pptp-strongvpn.html") and read about this problem in the comments.

---

