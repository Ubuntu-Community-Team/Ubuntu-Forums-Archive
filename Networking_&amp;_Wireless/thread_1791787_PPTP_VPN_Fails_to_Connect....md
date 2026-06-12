---
title: "PPTP VPN Fails to Connect..."
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by bknonix on 2011-06-27
Wondering if somebody can see what is going wrong here.

I have a Microsoft PPTP based VPN that works fine using WinXP clients.

I am running 11.04, have installed Network Manager and the PPTP, VPNC and PPTP-LINUX all installed and updated.

When I go to connect, it fails.   Here is the detailed SYSLOG - any ideas?

Jun 26 22:02:53 Laptop-6730b-BB NetworkManager[926]: <info> Starting VPN service 'pptp'...
Jun 26 22:02:53 Laptop-6730b-BB NetworkManager[926]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 2808
Jun 26 22:02:53 Laptop-6730b-BB NetworkManager[926]: <info> VPN service 'pptp' appeared; activating connections
Jun 26 22:02:53 Laptop-6730b-BB NetworkManager[926]: <info> VPN plugin state changed: 3
Jun 26 22:02:53 Laptop-6730b-BB pppd[2810]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jun 26 22:02:53 Laptop-6730b-BB NetworkManager[926]: <info> VPN connection 'NCE' (Connect) reply received.
Jun 26 22:02:53 Laptop-6730b-BB pppd[2810]: pppd 2.4.5 started by root, uid 0
Jun 26 22:02:53 Laptop-6730b-BB pppd[2810]: using channel 2
Jun 26 22:02:53 Laptop-6730b-BB pppd[2810]: Using interface ppp0
Jun 26 22:02:53 Laptop-6730b-BB pppd[2810]: Connect: ppp0 <--> /dev/pts/2
Jun 26 22:02:53 Laptop-6730b-BB NetworkManager[926]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 26 22:02:53 Laptop-6730b-BB NetworkManager[926]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jun 26 22:02:54 Laptop-6730b-BB pptp[2814]: nm-pptp-service-2808 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jun 26 22:02:54 Laptop-6730b-BB pptp[2821]: nm-pptp-service-2808 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jun 26 22:02:54 Laptop-6730b-BB pptp[2821]: nm-pptp-service-2808 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jun 26 22:02:54 Laptop-6730b-BB pptp[2821]: nm-pptp-service-2808 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jun 26 22:02:54 Laptop-6730b-BB pppd[2810]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x8298d90e> <pcomp> <accomp>]
Jun 26 22:02:55 Laptop-6730b-BB pptp[2821]: nm-pptp-service-2808 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jun 26 22:02:55 Laptop-6730b-BB pptp[2821]: nm-pptp-service-2808 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jun 26 22:02:55 Laptop-6730b-BB pptp[2821]: nm-pptp-service-2808 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 0).
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: rcvd [LCP ConfReq id=0x3 <mru 1400> <asyncmap 0x0> <auth pap> <magic 0x9fc5d33f> <pcomp> <accomp>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: sent [LCP ConfNak id=0x3 <auth chap MS-v2>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x8298d90e> <pcomp> <accomp>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: rcvd [LCP ConfReq id=0x4 <mru 1400> <asyncmap 0x0> <auth chap MS-v2> <magic 0x9fc5d33f> <pcomp> <accomp>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: sent [LCP ConfAck id=0x4 <mru 1400> <asyncmap 0x0> <auth chap MS-v2> <magic 0x9fc5d33f> <pcomp> <accomp>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: rcvd [CHAP Challenge id=0x5 <d22cd22cd22cd22cd22cd22cd22cd22c>, name = ""]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: sent [CHAP Response id=0x5 <7223ef4ff6b1d4610ac8c1f99b75de9f00000000000000007383387c176c2713697be805d241f152fdaad1874eca58fc00>, name = "masked"]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: rcvd [CHAP Success id=0x5 "S=B0C473FEC84F1A23EDFA20C9D05027A5C25129F0 M=Welcome to guest"]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: CHAP authentication succeeded
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: rcvd [CCP ConfReq id=0x6 <mppe +H -M +S -L -D -C>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: sent [CCP ConfAck id=0x6 <mppe +H -M +S -L -D -C>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: sent [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: rcvd [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: MPPE 128-bit stateless compression enabled
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfReq id=0x7 <addr 192.168.61.1>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfAck id=0x7 <addr 192.168.61.1>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfRej id=0x1 <ms-dns1 192.168.61.51> <ms-dns2 207.164.234.193>]
Jun 26 22:02:55 Laptop-6730b-BB pppd[2810]: Received bad configure-rej:  81 06 c0 a8 3d 33 83 06 cf a4 ea c1
Jun 26 22:02:58 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jun 26 22:02:58 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfReq id=0x8 <addr 192.168.61.1>]
Jun 26 22:02:58 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfAck id=0x8 <addr 192.168.61.1>]
Jun 26 22:02:58 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfRej id=0x1 <ms-dns1 192.168.61.51> <ms-dns2 207.164.234.193>]
Jun 26 22:02:58 Laptop-6730b-BB pppd[2810]: Received bad configure-rej:  81 06 c0 a8 3d 33 83 06 cf a4 ea c1
Jun 26 22:03:01 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jun 26 22:03:01 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfRej id=0x1 <ms-dns1 192.168.61.51> <ms-dns2 207.164.234.193>]
Jun 26 22:03:01 Laptop-6730b-BB pppd[2810]: Received bad configure-rej:  81 06 c0 a8 3d 33 83 06 cf a4 ea c1
Jun 26 22:03:01 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfReq id=0x9 <addr 192.168.61.1>]
Jun 26 22:03:01 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfAck id=0x9 <addr 192.168.61.1>]
Jun 26 22:03:04 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jun 26 22:03:04 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfRej id=0x1 <ms-dns1 192.168.61.51> <ms-dns2 207.164.234.193>]
Jun 26 22:03:04 Laptop-6730b-BB pppd[2810]: Received bad configure-rej:  81 06 c0 a8 3d 33 83 06 cf a4 ea c1
Jun 26 22:03:04 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfReq id=0xa <addr 192.168.61.1>]
Jun 26 22:03:04 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfAck id=0xa <addr 192.168.61.1>]
Jun 26 22:03:07 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jun 26 22:03:07 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfRej id=0x1 <ms-dns1 192.168.61.51> <ms-dns2 207.164.234.193>]
Jun 26 22:03:07 Laptop-6730b-BB pppd[2810]: Received bad configure-rej:  81 06 c0 a8 3d 33 83 06 cf a4 ea c1
Jun 26 22:03:07 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfReq id=0xb <addr 192.168.61.1>]
Jun 26 22:03:07 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfAck id=0xb <addr 192.168.61.1>]
Jun 26 22:03:10 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jun 26 22:03:10 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfRej id=0x1 <ms-dns1 192.168.61.51> <ms-dns2 207.164.234.193>]
Jun 26 22:03:10 Laptop-6730b-BB pppd[2810]: Received bad configure-rej:  81 06 c0 a8 3d 33 83 06 cf a4 ea c1
Jun 26 22:03:10 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfReq id=0xc <addr 192.168.61.1>]
Jun 26 22:03:10 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfAck id=0xc <addr 192.168.61.1>]
Jun 26 22:03:13 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jun 26 22:03:13 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfRej id=0x1 <ms-dns1 192.168.61.51> <ms-dns2 207.164.234.193>]
Jun 26 22:03:13 Laptop-6730b-BB pppd[2810]: Received bad configure-rej:  81 06 c0 a8 3d 33 83 06 cf a4 ea c1
Jun 26 22:03:13 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfReq id=0xd <addr 192.168.61.1>]
Jun 26 22:03:13 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfAck id=0xd <addr 192.168.61.1>]
Jun 26 22:03:15 Laptop-6730b-BB pppd[2810]: rcvd [LCP EchoReq id=0xe magic=0x9fc5d33f]
Jun 26 22:03:15 Laptop-6730b-BB pppd[2810]: sent [LCP EchoRep id=0xe magic=0x8298d90e]
Jun 26 22:03:16 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jun 26 22:03:16 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfRej id=0x1 <ms-dns1 192.168.61.51> <ms-dns2 207.164.234.193>]
Jun 26 22:03:16 Laptop-6730b-BB pppd[2810]: Received bad configure-rej:  81 06 c0 a8 3d 33 83 06 cf a4 ea c1
Jun 26 22:03:16 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfReq id=0xf <addr 192.168.61.1>]
Jun 26 22:03:16 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfAck id=0xf <addr 192.168.61.1>]
Jun 26 22:03:19 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jun 26 22:03:19 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfRej id=0x1 <ms-dns1 192.168.61.51> <ms-dns2 207.164.234.193>]
Jun 26 22:03:19 Laptop-6730b-BB pppd[2810]: Received bad configure-rej:  81 06 c0 a8 3d 33 83 06 cf a4 ea c1
Jun 26 22:03:20 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfReq id=0x10 <addr 192.168.61.1>]
Jun 26 22:03:20 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfAck id=0x10 <addr 192.168.61.1>]
Jun 26 22:03:22 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jun 26 22:03:22 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfRej id=0x1 <ms-dns1 192.168.61.51> <ms-dns2 207.164.234.193>]
Jun 26 22:03:22 Laptop-6730b-BB pppd[2810]: Received bad configure-rej:  81 06 c0 a8 3d 33 83 06 cf a4 ea c1
Jun 26 22:03:23 Laptop-6730b-BB pppd[2810]: rcvd [IPCP ConfReq id=0x11 <addr 192.168.61.1>]
Jun 26 22:03:23 Laptop-6730b-BB pppd[2810]: sent [IPCP ConfAck id=0x11 <addr 192.168.61.1>]
Jun 26 22:03:25 Laptop-6730b-BB pppd[2810]: IPCP: timeout sending Config-Requests
Jun 26 22:03:25 Laptop-6730b-BB pppd[2810]: MPPE disabled
Jun 26 22:03:25 Laptop-6730b-BB pppd[2810]: sent [LCP TermReq id=0x2 "MPPE disabled"]
Jun 26 22:03:25 Laptop-6730b-BB pppd[2810]: sent [LCP TermReq id=0x3 "MPPE disabled"]
Jun 26 22:03:25 Laptop-6730b-BB pppd[2810]: rcvd [LCP TermAck id=0x2]
Jun 26 22:03:25 Laptop-6730b-BB pppd[2810]: Connection terminated.
Jun 26 22:03:25 Laptop-6730b-BB NetworkManager[926]: <warn> VPN plugin failed: 1
Jun 26 22:03:25 Laptop-6730b-BB avahi-daemon[928]: Withdrawing workstation service for ppp0.
Jun 26 22:03:25 Laptop-6730b-BB NetworkManager[926]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 26 22:03:25 Laptop-6730b-BB pptp[2814]: nm-pptp-service-2808 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jun 26 22:03:25 Laptop-6730b-BB pptp[2814]: nm-pptp-service-2808 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jun 26 22:03:25 Laptop-6730b-BB pptp[2821]: nm-pptp-service-2808 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jun 26 22:03:25 Laptop-6730b-BB pptp[2821]: nm-pptp-service-2808 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jun 26 22:03:25 Laptop-6730b-BB pptp[2821]: nm-pptp-service-2808 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jun 26 22:03:25 Laptop-6730b-BB pppd[2810]: Script /usr/sbin/pptp masked.domain.org --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-2808 finished (pid 2812), status = 0x0
Jun 26 22:03:25 Laptop-6730b-BB pppd[2810]: Exit.
Jun 26 22:03:25 Laptop-6730b-BB NetworkManager[926]: <info> VPN plugin state changed: 6
Jun 26 22:03:25 Laptop-6730b-BB NetworkManager[926]: <info> VPN plugin state change reason: 0
Jun 26 22:03:25 Laptop-6730b-BB NetworkManager[926]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Jun 26 22:03:25 Laptop-6730b-BB NetworkManager[926]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun 26 22:03:30 Laptop-6730b-BB NetworkManager[926]: <info> VPN service 'pptp' disappeared

---

