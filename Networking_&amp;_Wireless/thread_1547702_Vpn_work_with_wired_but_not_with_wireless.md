---
title: "Vpn work with wired but not with wireless"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by HaajAli on 2010-08-07
Hi ;)
when i'm connected with wired (eth0) to my access point vpn connection connect flawless
but when connect with wireless (eth2) to the same access point vpn connection failed
i don't know whats the deal ....
i try disable eth0 (ifconfig eth0 down) . it's disabled now but vpn connection still didn't work :(

---

### Post by HaajAli on 2010-08-07
Any idea ? :(

---

### Post by gombadi on 2010-08-07
What vpn software are you using?

What messages appear in /var/log/syslog when the vpn fails to connect?

---

### Post by HaajAli on 2010-08-08
Hi and thanks for answering me ;)

i'm using PPTP tunneling protocol in network manager applet
here the result while i'm try to connect and show me connection failed :

```

Aug  8 23:19:57 *** NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Aug  8 23:19:57 *** NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 2885
Aug  8 23:19:57 *** NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Aug  8 23:19:57 *** NetworkManager: <info>  VPN plugin state changed: 1
Aug  8 23:20:01 *** NetworkManager: <info>  VPN plugin state changed: 3
Aug  8 23:20:01 *** NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received.
Aug  8 23:20:01 *** pppd[2890]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug  8 23:20:01 *** pppd[2890]: pppd 2.4.5 started by root, uid 0
Aug  8 23:20:01 *** pppd[2890]: Using interface ppp0
Aug  8 23:20:01 *** pppd[2890]: Connect: ppp0 <--> /dev/pts/1
Aug  8 23:20:01 *** pptp[2892]: nm-pptp-service-2885 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Aug  8 23:20:01 *** NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug  8 23:20:01 *** NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Aug  8 23:20:02 *** pptp[2898]: nm-pptp-service-2885 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Aug  8 23:20:03 *** pptp[2898]: nm-pptp-service-2885 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Aug  8 23:20:03 *** pptp[2898]: nm-pptp-service-2885 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Aug  8 23:20:03 *** pptp[2898]: nm-pptp-service-2885 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Aug  8 23:20:04 *** pptp[2898]: nm-pptp-service-2885 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Aug  8 23:20:04 *** pptp[2898]: nm-pptp-service-2885 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 48633).
Aug  8 23:20:06 *** kernel: [ 1471.669180] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=96 TOS=0x00 PREC=0x00 TTL=108 ID=1070 PROTO=47 
Aug  8 23:20:06 *** kernel: [ 1471.669365] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=56 TOS=0x00 PREC=0x00 TTL=108 ID=1071 PROTO=47 
Aug  8 23:20:07 *** kernel: [ 1472.488480] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=60 TOS=0x00 PREC=0x00 TTL=108 ID=1085 PROTO=47 
Aug  8 23:20:07 *** kernel: [ 1472.587801] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=92 TOS=0x00 PREC=0x00 TTL=108 ID=1447 PROTO=47 
Aug  8 23:20:09 *** kernel: [ 1474.945975] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=60 TOS=0x00 PREC=0x00 TTL=108 ID=1854 PROTO=47 
Aug  8 23:20:10 *** kernel: [ 1475.356186] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=92 TOS=0x00 PREC=0x00 TTL=108 ID=1856 PROTO=47 
Aug  8 23:20:12 *** kernel: [ 1477.813135] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=60 TOS=0x00 PREC=0x00 TTL=108 ID=2488 PROTO=47 
Aug  8 23:20:14 *** kernel: [ 1479.861102] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=92 TOS=0x00 PREC=0x00 TTL=108 ID=2632 PROTO=47 
Aug  8 23:20:15 *** kernel: [ 1480.680202] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=60 TOS=0x00 PREC=0x00 TTL=108 ID=2636 PROTO=47 
Aug  8 23:20:18 *** kernel: [ 1483.547318] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=92 TOS=0x00 PREC=0x00 TTL=108 ID=3666 PROTO=47 
Aug  8 23:20:18 *** kernel: [ 1483.547503] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=60 TOS=0x00 PREC=0x00 TTL=108 ID=3667 PROTO=47 
Aug  8 23:20:21 *** kernel: [ 1486.415249] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=60 TOS=0x00 PREC=0x00 TTL=108 ID=4176 PROTO=47 
Aug  8 23:20:22 *** kernel: [ 1487.643294] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=92 TOS=0x00 PREC=0x00 TTL=108 ID=4179 PROTO=47 
Aug  8 23:20:24 *** kernel: [ 1489.691200] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=60 TOS=0x00 PREC=0x00 TTL=108 ID=4694 PROTO=47 
Aug  8 23:20:26 *** kernel: [ 1491.739131] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=92 TOS=0x00 PREC=0x00 TTL=108 ID=4698 PROTO=47 
Aug  8 23:20:27 *** kernel: [ 1492.967856] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=60 TOS=0x00 PREC=0x00 TTL=108 ID=4711 PROTO=47 
Aug  8 23:20:30 *** kernel: [ 1495.835124] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=92 TOS=0x00 PREC=0x00 TTL=108 ID=5238 PROTO=47 
Aug  8 23:20:30 *** kernel: [ 1495.835363] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=60 TOS=0x00 PREC=0x00 TTL=108 ID=5239 PROTO=47 
Aug  8 23:20:32 *** pppd[2890]: LCP: timeout sending Config-Requests
Aug  8 23:20:32 *** pppd[2890]: Connection terminated.
Aug  8 23:20:32 *** NetworkManager: <info>  VPN plugin failed: 1
Aug  8 23:20:32 *** NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug  8 23:20:32 *** pppd[2890]: Modem hangup
Aug  8 23:20:32 *** pptp[2892]: nm-pptp-service-2885 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Aug  8 23:20:32 *** pptp[2892]: nm-pptp-service-2885 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Aug  8 23:20:32 *** pptp[2898]: nm-pptp-service-2885 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Aug  8 23:20:32 *** pptp[2898]: nm-pptp-service-2885 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Aug  8 23:20:32 *** pptp[2898]: nm-pptp-service-2885 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Aug  8 23:20:32 *** NetworkManager: <info>  VPN plugin failed: 1
Aug  8 23:20:32 *** pppd[2890]: Exit.
Aug  8 23:20:32 *** NetworkManager: <info>  VPN plugin failed: 1
Aug  8 23:20:32 *** NetworkManager: <info>  VPN plugin state changed: 6
Aug  8 23:20:32 *** NetworkManager: <info>  VPN plugin state change reason: 0
Aug  8 23:20:32 *** NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Aug  8 23:20:32 *** NetworkManager: <info>  (eth2): writing resolv.conf to /sbin/resolvconf
Aug  8 23:20:32 *** NetworkManager: <info>  Policy set 'Wireless connection 1' (eth2) as default for routing and DNS.
Aug  8 23:20:43 *** wpa_supplicant[833]: CTRL-EVENT-SCAN-RESULTS 
Aug  8 23:20:45 *** NetworkManager: <debug> [1281293445.002759] ensure_killed(): waiting for vpn service pid 2885 to exit
Aug  8 23:20:45 *** NetworkManager: <debug> [1281293445.003074] ensure_killed(): vpn service pid 2885 cleaned up

```

---

### Post by gombadi on 2010-08-08
> 
Aug  8 23:20:04 *** pptp[2898]: nm-pptp-service-2885 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 48633).
Aug  8 23:20:06 *** kernel: [ 1471.669180] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=96 TOS=0x00 PREC=0x00 TTL=108 ID=1070 PROTO=47 
...
Aug  8 23:20:30 *** kernel: [ 1495.835363] Inbound IN=eth2 OUT= MAC=xxx SRC=[my vpn gateway] DST=192.168.1.7 LEN=60 TOS=0x00 PREC=0x00 TTL=108 ID=5239 PROTO=47 
Aug  8 23:20:32 *** pppd[2890]: LCP: timeout sending Config-Requests
Aug  8 23:20:32 *** pppd[2890]: Connection terminated.


The lines in the middle look like the output from the firewall. Have you checked that the vpn can send and receive packets over eth2?

---

### Post by HaajAli on 2010-08-09
Hi gombadi thanks so much for answering and saving me :D
yes i'm installed a firewall about 2 month ago and i forget that :p
i disable my firewall and vpn connect correctly
but i don't know yet how i was connect with wired !
it's means firewall block just the vpn connection over eth2 :-? and i never mind connection faild because of firewall block it 
thank you alot ! :KS

---

