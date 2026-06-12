---
title: "VPN over wireless - x86_64 desktop on Dell laptop"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by eqbalz on 2010-09-26
I recently installed Ubuntu 10.04. My PPTP VPN connection works when I am connected to my router at home using a wire, but it does not work when I am on wireless.

Here is the output from syslog:

```
Sep 26 14:40:21 ubuntu-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Sep 26 14:40:21 ubuntu-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 3007
Sep 26 14:40:21 ubuntu-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Sep 26 14:40:21 ubuntu-desktop NetworkManager: <info>  VPN plugin state changed: 1
Sep 26 14:40:26 ubuntu-desktop NetworkManager: <info>  VPN plugin state changed: 3
Sep 26 14:40:26 ubuntu-desktop NetworkManager: <info>  VPN connection 'MY VPN' (Connect) reply received.
Sep 26 14:40:26 ubuntu-desktop pppd[3010]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Sep 26 14:40:26 ubuntu-desktop pppd[3010]: pppd 2.4.5 started by root, uid 0
Sep 26 14:40:26 ubuntu-desktop pppd[3010]: Using interface ppp0
Sep 26 14:40:26 ubuntu-desktop pppd[3010]: Connect: ppp0 <--> /dev/pts/0
Sep 26 14:40:26 ubuntu-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 26 14:40:26 ubuntu-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Sep 26 14:40:26 ubuntu-desktop pptp[3013]: nm-pptp-service-3007 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Sep 26 14:40:26 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Sep 26 14:40:26 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Sep 26 14:40:26 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Sep 26 14:40:27 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Sep 26 14:40:27 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Sep 26 14:40:27 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 5597).
Sep 26 14:40:27 ubuntu-desktop kernel: [ 4442.851186] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=59 TOS=0x00 PREC=0x00 TTL=240 ID=18723 PROTO=47 
Sep 26 14:40:27 ubuntu-desktop kernel: [ 4442.851740] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=60 TOS=0x00 PREC=0x00 TTL=240 ID=18725 PROTO=47 
Sep 26 14:40:29 ubuntu-desktop kernel: [ 4444.840573] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=59 TOS=0x00 PREC=0x00 TTL=240 ID=19265 PROTO=47 
Sep 26 14:40:30 ubuntu-desktop kernel: [ 4445.750449] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=60 TOS=0x00 PREC=0x00 TTL=240 ID=19375 PROTO=47 
Sep 26 14:40:31 ubuntu-desktop kernel: [ 4446.863724] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=59 TOS=0x00 PREC=0x00 TTL=240 ID=19574 PROTO=47 
Sep 26 14:40:33 ubuntu-desktop kernel: [ 4448.746413] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=60 TOS=0x00 PREC=0x00 TTL=240 ID=19899 PROTO=47 
Sep 26 14:40:33 ubuntu-desktop kernel: [ 4448.865395] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=59 TOS=0x00 PREC=0x00 TTL=240 ID=19912 PROTO=47 
Sep 26 14:40:35 ubuntu-desktop kernel: [ 4450.877360] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=59 TOS=0x00 PREC=0x00 TTL=240 ID=20228 PROTO=47 
Sep 26 14:40:36 ubuntu-desktop kernel: [ 4451.771678] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=60 TOS=0x00 PREC=0x00 TTL=240 ID=20356 PROTO=47 
Sep 26 14:40:37 ubuntu-desktop kernel: [ 4452.889902] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=59 TOS=0x00 PREC=0x00 TTL=240 ID=20468 PROTO=47 
Sep 26 14:40:39 ubuntu-desktop kernel: [ 4454.746436] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=60 TOS=0x00 PREC=0x00 TTL=240 ID=20724 PROTO=47 
Sep 26 14:40:39 ubuntu-desktop kernel: [ 4454.902222] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=59 TOS=0x00 PREC=0x00 TTL=240 ID=20749 PROTO=47 
Sep 26 14:40:41 ubuntu-desktop kernel: [ 4456.914528] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=59 TOS=0x00 PREC=0x00 TTL=240 ID=21037 PROTO=47 
Sep 26 14:40:42 ubuntu-desktop kernel: [ 4457.742587] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=60 TOS=0x00 PREC=0x00 TTL=240 ID=21208 PROTO=47 
Sep 26 14:40:43 ubuntu-desktop kernel: [ 4458.926759] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=59 TOS=0x00 PREC=0x00 TTL=240 ID=21311 PROTO=47 
Sep 26 14:40:45 ubuntu-desktop kernel: [ 4460.735963] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=60 TOS=0x00 PREC=0x00 TTL=240 ID=21585 PROTO=47 
Sep 26 14:40:45 ubuntu-desktop kernel: [ 4460.939265] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=59 TOS=0x00 PREC=0x00 TTL=240 ID=21613 PROTO=47 
Sep 26 14:40:47 ubuntu-desktop kernel: [ 4462.956023] Inbound IN=wlan0 OUT= MAC=00:55:14:cc:ff:30:00:14:bf:ad:5d:da:08:00 SRC=71.65.209.31 DST=192.168.103.104 LEN=44 TOS=0x00 PREC=0x00 TTL=240 ID=21838 PROTO=47 
Sep 26 14:40:47 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[ctrlp_disp:pptp_ctrl.c:929]: Call disconnect notification received (call id 5597)
Sep 26 14:40:47 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[ctrlp_disp:pptp_ctrl.c:788]: Received Stop Control Connection Request.
Sep 26 14:40:47 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 4 'Stop-Control-Connection-Reply'
Sep 26 14:40:47 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Sep 26 14:40:47 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Sep 26 14:40:47 ubuntu-desktop pptp[3021]: nm-pptp-service-3007 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Sep 26 14:40:47 ubuntu-desktop pppd[3010]: Modem hangup
Sep 26 14:40:47 ubuntu-desktop pppd[3010]: Connection terminated.
Sep 26 14:40:47 ubuntu-desktop NetworkManager: <info>  VPN plugin failed: 1
Sep 26 14:40:47 ubuntu-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 26 14:40:47 ubuntu-desktop pppd[3010]: Exit.
Sep 26 14:40:47 ubuntu-desktop NetworkManager: <info>  VPN plugin failed: 1
Sep 26 14:40:47 ubuntu-desktop NetworkManager: <info>  VPN plugin failed: 1
Sep 26 14:40:47 ubuntu-desktop NetworkManager: <info>  VPN plugin state changed: 6
Sep 26 14:40:47 ubuntu-desktop NetworkManager: <info>  VPN plugin state change reason: 0
Sep 26 14:40:47 ubuntu-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Sep 26 14:40:47 ubuntu-desktop NetworkManager: <info>  Policy set 'Home' (wlan0) as default for routing and DNS.

```

---

