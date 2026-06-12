---
title: "3G connection suddenly stopped working"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by diazamet on 2010-03-18
System spec:
Dell XPS M1330
Ubuntu Karmic 9.10
Huawei E160 HSDPA modem
ISP: T-Mobile Germany

This maybe coincidence but since doing an *apt-get update/upgrade* yesterday (17/03/2010 at ~13:00CET) I am no longer able to connect using my 3G modem.
Looking at syslog, pppd appears to do the CHAP authentication, then request IP address after which there is a modem hangup message.

Previously I did not have to do anything special, I just set up the connection in Network Manager and it "just worked".

I noticed the **Protocol-Reject for 'Compression Control Protocol'** line and I have since tried removing the compression options to no avail.

Is this even a problem with my setup?  Could it be a problem at the ISP?  I suspect not as I have a Nexus One on the same network and there has been no disruption to the service.

A friend is also running Karmic, has the same modem, same provider, did the same apt-get update, and he is also no longer able to connect.

Here is my log file entries from Network Manager/pppd...
```
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) starting connection 'T-mobile (D1)'
Mar 18 10:30:17 tails NetworkManager: <info>  (ttyUSB1): device state change: 3 -> 4 (reason 0)
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Mar 18 10:30:17 tails modem-manager: (ttyUSB1) opening serial device...
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) scheduled...
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) starting...
Mar 18 10:30:17 tails NetworkManager: <info>  (ttyUSB1): device state change: 4 -> 5 (reason 0)
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) successful.
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) complete.
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) started...
Mar 18 10:30:17 tails NetworkManager: <info>  (ttyUSB1): device state change: 5 -> 7 (reason 0)
Mar 18 10:30:17 tails NetworkManager: <info>  Starting pppd connection
Mar 18 10:30:17 tails NetworkManager: <debug> [1268904617.577276] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB1 noipdefault noauth usepeerdns lcp-echo-failure 5 lcp-echo-interval 30 ipparam /org/freedesktop/NetworkManager/PPP/26 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Mar 18 10:30:17 tails NetworkManager: <debug> [1268904617.578865] nm_ppp_manager_start(): ppp started with pid 6625
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) complete.
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP6 Configure Get) started...
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 18 10:30:17 tails pppd[6625]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Mar 18 10:30:17 tails pppd[6625]: pppd 2.4.5 started by root, uid 0
Mar 18 10:30:17 tails pppd[6625]: using channel 27
Mar 18 10:30:17 tails NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar 18 10:30:17 tails NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Mar 18 10:30:17 tails pppd[6625]: Using interface ppp0
Mar 18 10:30:17 tails pppd[6625]: Connect: ppp0 <--> /dev/ttyUSB1
Mar 18 10:30:17 tails pppd[6625]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xb2906fea> <pcomp> <accomp>]
Mar 18 10:30:17 tails pppd[6625]: rcvd [LCP ConfReq id=0x13 <asyncmap 0x0> <auth chap MD5> <magic 0x143f936> <pcomp> <accomp>]
Mar 18 10:30:17 tails pppd[6625]: sent [LCP ConfAck id=0x13 <asyncmap 0x0> <auth chap MD5> <magic 0x143f936> <pcomp> <accomp>]
Mar 18 10:30:17 tails pppd[6625]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xb2906fea> <pcomp> <accomp>]
Mar 18 10:30:17 tails pppd[6625]: sent [LCP EchoReq id=0x0 magic=0xb2906fea]
Mar 18 10:30:17 tails pppd[6625]: rcvd [LCP DiscReq id=0x14 magic=0x143f936]
Mar 18 10:30:17 tails pppd[6625]: rcvd [CHAP Challenge id=0x1 <143dc5c6fe512dbfc05c62382a5eb7c1>, name = "UMTS_CHAP_SRVR"]
Mar 18 10:30:17 tails pppd[6625]: sent [CHAP Response id=0x1 <f57d4e37b19220591a08ee84db111462>, name = ""]
Mar 18 10:30:17 tails pppd[6625]: rcvd [LCP EchoRep id=0x0 magic=0x143f936 b2 90 6f ea]
Mar 18 10:30:17 tails pppd[6625]: rcvd [CHAP Success id=0x1 ""]
Mar 18 10:30:17 tails pppd[6625]: CHAP authentication succeeded
Mar 18 10:30:17 tails pppd[6625]: CHAP authentication succeeded
Mar 18 10:30:17 tails pppd[6625]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Mar 18 10:30:17 tails pppd[6625]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Mar 18 10:30:17 tails pppd[6625]: rcvd [LCP ProtRej id=0x15 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Mar 18 10:30:17 tails pppd[6625]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Mar 18 10:30:17 tails pppd[6625]: Modem hangup
Mar 18 10:30:17 tails pppd[6625]: Connection terminated.
Mar 18 10:30:17 tails NetworkManager: <info>  (ttyUSB1): device state change: 7 -> 9 (reason 13)
Mar 18 10:30:17 tails NetworkManager: <info>  Marking connection 'T-mobile (D1)' invalid.
Mar 18 10:30:17 tails NetworkManager: <info>  Activation (ttyUSB1) failed.
Mar 18 10:30:17 tails NetworkManager: <info>  (ttyUSB1): device state change: 9 -> 3 (reason 0)
Mar 18 10:30:17 tails NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 0).
Mar 18 10:30:17 tails modem-manager: (ttyUSB1) closing serial device...
Mar 18 10:30:17 tails NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Mar 18 10:30:17 tails NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Mar 18 10:30:17 tails NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Mar 18 10:30:18 tails pppd[6625]: Exit.
Mar 18 10:30:20 tails NetworkManager: <debug> [1268904620.001276] ensure_killed(): waiting for ppp pid 6625 to exit
Mar 18 10:30:20 tails NetworkManager: <debug> [1268904620.001409] ensure_killed(): ppp pid 6625 cleaned up
```

It previously mentioned upgrade updated the following packages:
```
chromium-browser (5.0.356.0~svn20100317r41807-0ubuntu1~ucd1~karmic) ...
chromium-browser-inspector (5.0.356.0~svn20100317r41807-0ubuntu1~ucd1~karmic) ...
linux-image-2.6.31-20-generic (2.6.31-20.58) ...
libpoppler5 (0.12.0-0ubuntu2.2) ...
libpoppler-glib4 (0.12.0-0ubuntu2.2) ...
libpoppler-qt4-3 (0.12.0-0ubuntu2.2) ...
linux-headers-2.6.31-20 (2.6.31-20.58) ...
linux-headers-2.6.31-20-generic (2.6.31-20.58) ...
linux-libc-dev (2.6.31-20.58) ...
poppler-utils (0.12.0-0ubuntu2.2) ...
```

---

### Post by alexfish on 2010-03-18
hi

one thing of note is the ppp is trying to connect on tttyusb1

I would normally see ttyusb0 or ttyusb2

have you tried deleting the existing connection then make new connection via NM
also have you cleaned up the configs etc after the updates

 try these command from the terminal

dmesg | grep -e "modem" -e "tty" 

to verify the ports used by the device,  disconnect and reconnect the device and hopefully get it to settle with ttyusb0 and ttyusb1, then try the connection

then this command from another terminal

tail -f /var/log/syslog

monitor what is happening

do you have usb modeswitch installed

regards

alexfish

---

