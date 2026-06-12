---
title: "pptp connections keeps failing"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by byenary on 2010-09-10
Hello,

I got this working om my laptop but on my desktop this keeps going wrong, its an upgraded system to 10.04.
Made a standard pptp connection using network-manager (and the connection is 100% fine, working on laptop and on windoooz machine)
This is syslog any ideas, i reinstalled network-manager-pptp and pptp-gnome, but no go no go..

hero@hardyhero:/var/log$ tail -f syslog
Sep 10 09:14:15 hardyhero kernel: [  170.122505] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=96 TOS=0x00 PREC=0x00 TTL=113 ID=10627 PROTO=47 
Sep 10 09:14:17 hardyhero kernel: [  172.124143] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=92 TOS=0x00 PREC=0x00 TTL=114 ID=10649 PROTO=47 
Sep 10 09:14:18 hardyhero kernel: [  173.054745] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=60 TOS=0x00 PREC=0x00 TTL=113 ID=10666 PROTO=47 
Sep 10 09:14:20 hardyhero kernel: [  175.134305] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=92 TOS=0x00 PREC=0x00 TTL=114 ID=10709 PROTO=47 
Sep 10 09:14:21 hardyhero kernel: [  176.054432] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=60 TOS=0x00 PREC=0x00 TTL=113 ID=10722 PROTO=47 
Sep 10 09:14:24 hardyhero kernel: [  179.057979] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=60 TOS=0x00 PREC=0x00 TTL=113 ID=10750 PROTO=47 
Sep 10 09:14:24 hardyhero kernel: [  179.136316] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=92 TOS=0x00 PREC=0x00 TTL=114 ID=10751 PROTO=47 
Sep 10 09:14:27 hardyhero kernel: [  182.061881] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=60 TOS=0x00 PREC=0x00 TTL=113 ID=10788 PROTO=47 
Sep 10 09:14:28 hardyhero kernel: [  183.124591] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=92 TOS=0x00 PREC=0x00 TTL=114 ID=10799 PROTO=47 
Sep 10 09:14:30 hardyhero kernel: [  185.067734] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=60 TOS=0x00 PREC=0x00 TTL=113 ID=10827 PROTO=47 
Sep 10 09:14:32 hardyhero kernel: [  187.130715] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=92 TOS=0x00 PREC=0x00 TTL=114 ID=10838 PROTO=47 
Sep 10 09:14:33 hardyhero kernel: [  188.071064] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=60 TOS=0x00 PREC=0x00 TTL=113 ID=10853 PROTO=47 
Sep 10 09:14:36 hardyhero kernel: [  191.069065] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=60 TOS=0x00 PREC=0x00 TTL=113 ID=10892 PROTO=47 
Sep 10 09:14:36 hardyhero kernel: [  191.130821] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=92 TOS=0x00 PREC=0x00 TTL=114 ID=10895 PROTO=47 
Sep 10 09:14:39 hardyhero kernel: [  194.074219] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=60 TOS=0x00 PREC=0x00 TTL=113 ID=10924 PROTO=47 
Sep 10 09:14:40 hardyhero kernel: [  195.136885] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=92 TOS=0x00 PREC=0x00 TTL=114 ID=10935 PROTO=47 
Sep 10 09:14:42 hardyhero kernel: [  197.076222] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=60 TOS=0x00 PREC=0x00 TTL=113 ID=10947 PROTO=47 
Sep 10 09:14:44 hardyhero kernel: [  199.140030] Inbound IN=eth0 OUT= MAC=00:1c:c0:21:1d:40:00:16:b6:87:6a:56:08:00 SRC=212.241.39.126 DST=192.168.123.61 LEN=92 TOS=0x00 PREC=0x00 TTL=114 ID=10974 PROTO=47 
Sep 10 09:14:45 hardyhero pppd[5419]: LCP: timeout sending Config-Requests
Sep 10 09:14:45 hardyhero pppd[5419]: Connection terminated.
Sep 10 09:14:45 hardyhero NetworkManager: <info>  VPN plugin failed: 1
Sep 10 09:14:45 hardyhero NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 10 09:14:45 hardyhero pptp[5424]: nm-pptp-service-5416 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Sep 10 09:14:45 hardyhero pptp[5424]: nm-pptp-service-5416 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Sep 10 09:14:45 hardyhero pppd[5419]: Modem hangup
Sep 10 09:14:45 hardyhero pptp[5439]: nm-pptp-service-5416 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Sep 10 09:14:45 hardyhero pptp[5439]: nm-pptp-service-5416 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Sep 10 09:14:45 hardyhero pptp[5439]: nm-pptp-service-5416 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Sep 10 09:14:45 hardyhero NetworkManager: <info>  VPN plugin failed: 1
Sep 10 09:14:45 hardyhero pppd[5419]: Exit.
Sep 10 09:14:45 hardyhero NetworkManager: <info>  VPN plugin failed: 1
Sep 10 09:14:45 hardyhero NetworkManager: <info>  VPN plugin state changed: 6
Sep 10 09:14:45 hardyhero NetworkManager: <info>  VPN plugin state change reason: 0
Sep 10 09:14:45 hardyhero NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Sep 10 09:14:45 hardyhero NetworkManager: <info>  Policy set 'Ifupdown (eth0)' (eth0) as default for routing and DNS.
Sep 10 09:14:57 hardyhero NetworkManager: <debug> [1284102897.002598] ensure_killed(): waiting for vpn service pid 5416 to exit
Sep 10 09:14:57 hardyhero NetworkManager: <debug> [1284102897.002715] ensure_killed(): vpn service pid 5416 cleaned up

---

### Post by utilitytrack on 2010-09-13
Hello, try completely turn off firewall:

```
# iptables -F && iptables -P INPUT ACCEPT && iptables -P FORWARD ACCEPT && iptables -P OUTPUT ACCEPT
```

---

