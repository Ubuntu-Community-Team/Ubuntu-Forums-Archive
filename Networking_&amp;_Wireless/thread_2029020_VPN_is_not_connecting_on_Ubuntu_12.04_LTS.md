---
title: "VPN is not connecting on Ubuntu 12.04 LTS"
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by moogs37 on 2012-07-19
Hello everyone. I have installed Ubuntu 12.04 LTS alongside Windows 7 on an HP Pavillion g7 laptop. I can connect to my network but I cannot connect to my VPN. I have tried several solutions that still, unfortunately, do not fix my problem.
 
Listed below are the logs that I am getting in the system. 
 
moogs@ubuntu:~$ tail -f /var/log/syslog
Jul 17 21:04:23 ubuntu pptp[3297]: nm-pptp-service-3282 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jul 17 21:04:23 ubuntu pptp[3297]: nm-pptp-service-3282 log[call_callbackptp_callmgr.c:79]: Closing connection (call state)
Jul 17 21:04:23 ubuntu NetworkManager[3016]: <warn> VPN plugin failed: 1
Jul 17 21:04:23 ubuntu pppd[3286]: Exit.
Jul 17 21:04:23 ubuntu NetworkManager[3016]: <warn> VPN plugin failed: 1
Jul 17 21:04:23 ubuntu NetworkManager[3016]: <info> VPN plugin state changed: stopped (6)
Jul 17 21:04:23 ubuntu NetworkManager[3016]: <info> VPN plugin state change reason: 0
Jul 17 21:04:23 ubuntu NetworkManager[3016]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jul 17 21:04:23 ubuntu NetworkManager[3016]: <info> Policy set 'WINGO' (wlan0) as default for IPv4 routing and DNS.
Jul 17 21:04:29 ubuntu NetworkManager[3016]: <info> VPN service 'pptp' disappeared
Jul 17 21:09:13 ubuntu NetworkManager[3016]: <info> Starting VPN service 'pptp'...
Jul 17 21:09:13 ubuntu NetworkManager[3016]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 3318
Jul 17 21:09:13 ubuntu NetworkManager[3016]: <info> VPN service 'pptp' appeared; activating connections
Jul 17 21:09:13 ubuntu NetworkManager[3016]: <info> VPN plugin state changed: init (1)
Jul 17 21:09:13 ubuntu NetworkManager[3016]: <info> VPN plugin state changed: starting (3)
Jul 17 21:09:13 ubuntu pppd[3322]: Plugin /usr/lib/pppd/2.4.5/nm-pptp-pppd-plugin.so loaded.
Jul 17 21:09:13 ubuntu NetworkManager[3016]: <info> VPN connection 'ACE MIAMI, FL' (Connect) reply received.
Jul 17 21:09:13 ubuntu pppd[3322]: pppd 2.4.5 started by root, uid 0
Jul 17 21:09:13 ubuntu pppd[3322]: Using interface ppp0
Jul 17 21:09:13 ubuntu pppd[3322]: Connect: ppp0 <--> /dev/pts/1
Jul 17 21:09:13 ubuntu pptp[3325]: nm-pptp-service-3318 log[mainptp.c:314]: The synchronous pptp option is NOT activated
Jul 17 21:09:13 ubuntu NetworkManager[3016]: SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 17 21:09:13 ubuntu NetworkManager[3016]: SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jul 17 21:09:13 ubuntu pptp[3333]: nm-pptp-service-3318 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jul 17 21:09:13 ubuntu pptp[3333]: nm-pptp-service-3318 log[ctrlp_dispptp_ctrl.c:739]: Received Start Control Connection Reply
Jul 17 21:09:13 ubuntu pptp[3333]: nm-pptp-service-3318 log[ctrlp_dispptp_ctrl.c:773]: Client connection established.
Jul 17 21:09:14 ubuntu pptp[3333]: nm-pptp-service-3318 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jul 17 21:09:14 ubuntu pptp[3333]: nm-pptp-service-3318 log[ctrlp_dispptp_ctrl.c:858]: Received Outgoing Call Reply.
Jul 17 21:09:14 ubuntu pptp[3333]: nm-pptp-service-3318 log[ctrlp_dispptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 17536).
Jul 17 21:09:14 ubuntu kernel: [ 1216.490280] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=61 TOS=0x00 PREC=0x20 TTL=50 ID=29515 DF PROTO=47
Jul 17 21:09:14 ubuntu kernel: [ 1216.517595] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=29516 DF PROTO=47
Jul 17 21:09:17 ubuntu kernel: [ 1219.429384] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=29517 DF PROTO=47
Jul 17 21:09:17 ubuntu kernel: [ 1219.484466] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=61 TOS=0x00 PREC=0x20 TTL=50 ID=29518 DF PROTO=47
Jul 17 21:09:20 ubuntu kernel: [ 1222.431411] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=29519 DF PROTO=47
Jul 17 21:09:20 ubuntu kernel: [ 1222.480571] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=61 TOS=0x00 PREC=0x20 TTL=50 ID=29520 DF PROTO=47
Jul 17 21:09:23 ubuntu kernel: [ 1225.422462] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=29521 DF PROTO=47
Jul 17 21:09:23 ubuntu kernel: [ 1225.474154] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=61 TOS=0x00 PREC=0x20 TTL=50 ID=29522 DF PROTO=47
Jul 17 21:09:26 ubuntu kernel: [ 1228.418027] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=29523 DF PROTO=47
Jul 17 21:09:26 ubuntu kernel: [ 1228.469107] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=61 TOS=0x00 PREC=0x20 TTL=50 ID=29524 DF PROTO=47
Jul 17 21:09:29 ubuntu kernel: [ 1231.415790] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=29525 DF PROTO=47
Jul 17 21:09:29 ubuntu kernel: [ 1231.464606] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=61 TOS=0x00 PREC=0x20 TTL=50 ID=29526 DF PROTO=47
Jul 17 21:09:32 ubuntu kernel: [ 1234.410720] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=29527 DF PROTO=47
Jul 17 21:09:32 ubuntu kernel: [ 1234.458517] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=61 TOS=0x00 PREC=0x20 TTL=50 ID=29528 DF PROTO=47
Jul 17 21:09:35 ubuntu kernel: [ 1237.409348] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=29529 DF PROTO=47
Jul 17 21:09:35 ubuntu kernel: [ 1237.454121] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=61 TOS=0x00 PREC=0x20 TTL=50 ID=29530 DF PROTO=47
Jul 17 21:09:38 ubuntu kernel: [ 1240.416825] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=29531 DF PROTO=47
Jul 17 21:09:38 ubuntu kernel: [ 1240.448252] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=61 TOS=0x00 PREC=0x20 TTL=50 ID=29532 DF PROTO=47
Jul 17 21:09:41 ubuntu kernel: [ 1243.412005] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=60 TOS=0x00 PREC=0x20 TTL=50 ID=29533 DF PROTO=47
Jul 17 21:09:41 ubuntu kernel: [ 1243.443033] Inbound IN=wlan0 OUT= MAC=cc:af:78:13:d5:67:00:18:39:3e:b5:6e:08:00 SRC=173.44.35.14 DST=192.168.1.107 LEN=61 TOS=0x00 PREC=0x20 TTL=50 ID=29534 DF PROTO=47
Jul 17 21:09:44 ubuntu pppd[3322]: LCP: timeout sending Config-Requests
Jul 17 21:09:44 ubuntu pppd[3322]: Connection terminated.
Jul 17 21:09:44 ubuntu avahi-daemon[1047]: Withdrawing workstation service for ppp0.
Jul 17 21:09:44 ubuntu NetworkManager[3016]: SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul 17 21:09:44 ubuntu NetworkManager[3016]: <warn> VPN plugin failed: 1
Jul 17 21:09:44 ubuntu pptp[3325]: nm-pptp-service-3318 warn[decaps_hdlcptp_gre.c:204]: short read (-1): Input/output error
Jul 17 21:09:44 ubuntu pptp[3325]: nm-pptp-service-3318 warn[decaps_hdlcptp_gre.c:216]: pppd may have shutdown, see pppd log
Jul 17 21:09:44 ubuntu pppd[3322]: Modem hangup
Jul 17 21:09:44 ubuntu pptp[3333]: nm-pptp-service-3318 log[callmgr_mainptp_callmgr.c:234]: Closing connection (unhandled)
Jul 17 21:09:44 ubuntu pptp[3333]: nm-pptp-service-3318 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jul 17 21:09:44 ubuntu pptp[3333]: nm-pptp-service-3318 log[call_callbackptp_callmgr.c:79]: Closing connection (call state)
Jul 17 21:09:44 ubuntu pppd[3322]: Exit.
Jul 17 21:09:44 ubuntu NetworkManager[3016]: <warn> VPN plugin failed: 1
Jul 17 21:09:44 ubuntu NetworkManager[3016]: <warn> VPN plugin failed: 1
Jul 17 21:09:44 ubuntu NetworkManager[3016]: <info> VPN plugin state changed: stopped (6)
Jul 17 21:09:44 ubuntu NetworkManager[3016]: <info> VPN plugin state change reason: 0
Jul 17 21:09:44 ubuntu NetworkManager[3016]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jul 17 21:09:44 ubuntu NetworkManager[3016]: <info> Policy set 'WINGO' (wlan0) as default for IPv4 routing and DNS.
Jul 17 21:09:49 ubuntu NetworkManager[3016]: <info> VPN service 'pptp' disappeared

---

### Post by Vitruvian Man on 2012-08-10
Go [here](https://wiki.ubuntu.com/VPN) and scroll down to where it says "VPN setup using the command line."

This helped me solve my problem in 12.04 and I hope it helps you as well.

---

