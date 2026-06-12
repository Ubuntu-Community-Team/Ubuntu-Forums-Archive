---
title: "Problem connecting to PPTP VPN"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by sun811 on 2009-02-09
Trying to connect to my ISP VPN using pptp-network-manager. This utility used to work fine with another provider, but it does not with my new provider. Meanwhile I'm able to connect in Windows. The only piece of information I got about the VPN is that it uses PAP authentication. I tried changing different options, switched on and off chap and chap MS-v2 encryption but the result is still the same - VPN connection error. Below is the content of my syslog file in its part related to establishing the VPN connection.
It is clear that after this point :

Feb  8 17:23:24 ecdesktop pppd[6235]: nm-pppd-plugin: CHAP check hook

my workstation and the ISP server try different options of authenticating but eventually fail. Could someone provide me with a hint what I can do to resolve the problem? Many thanks!

Evgeny



Feb  8 17:23:13 ecdesktop NetworkManager: <debug> [1234102993.393400] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of VPN connection 'lanck' 
Feb  8 17:23:13 ecdesktop NetworkManager: <debug> [1234102993.398520] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of VPN connection 'lanck' 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  Will activate VPN connection 'lanck', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'evgueni', vpn_data 'ppp-connection-type / pptp / pptp-remote / vpn.mylanck.net / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / yes / ppp-refuse-eap / yes / ppp-refuse-chap / yes / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''. 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 1 of 4 (Connection Prepare) scheduled... 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 6226) 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 1 of 4 (Connection Prepare) complete. 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6. 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 2 of 4 (Connection Prepare Wait) complete. 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 3 of 4 (Connect) scheduled... 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 3 of 4 (Connect) sending connect request. 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 3 of 4 (Connect) reply received. 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Feb  8 17:23:22 ecdesktop NetworkManager: <info>  VPN Activation (lanck) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Feb  8 17:23:22 ecdesktop pppd[6227]: Plugin nm-pppd-plugin.so loaded.
Feb  8 17:23:22 ecdesktop pppd[6227]: nm-pppd-plugin: plugin initialized.
Feb  8 17:23:23 ecdesktop kernel: [  341.759260] PPP generic driver version 2.4.2
Feb  8 17:23:23 ecdesktop pppd[6235]: pppd 2.4.4 started by root, uid 0
Feb  8 17:23:23 ecdesktop pptp[6238]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Feb  8 17:23:23 ecdesktop pptp[6241]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Feb  8 17:23:23 ecdesktop pptp[6241]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Feb  8 17:23:23 ecdesktop pptp[6241]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Feb  8 17:23:23 ecdesktop pppd[6235]: using channel 1
Feb  8 17:23:23 ecdesktop pppd[6235]: Using interface ppp0
Feb  8 17:23:23 ecdesktop pppd[6235]: Connect: ppp0 <--> /dev/pts/0
Feb  8 17:23:24 ecdesktop pptp[6241]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Feb  8 17:23:24 ecdesktop pptp[6241]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Feb  8 17:23:24 ecdesktop pptp[6241]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 27907). 
Feb  8 17:23:24 ecdesktop pppd[6235]: nm-pppd-plugin: CHAP check hook.
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfReq id=0x1 <mru 1416> <asyncmap 0x0> <magic 0xb5c64375> <pcomp> <accomp>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0x1 <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfNak id=0x1 <auth chap MS-v2>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfNak id=0x1 <mru 1500>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0xb5c64375> <pcomp> <accomp>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0x2 <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfNak id=0x2 <auth chap MS-v2>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0xb5c64375> <pcomp> <accomp>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0x3 <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfNak id=0x3 <auth chap MS-v2>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0x4 <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfNak id=0x4 <auth chap MS-v2>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0x5 <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfNak id=0x5 <auth chap MS-v2>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0x6 <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfRej id=0x6 <auth pap>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0x7 <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfRej id=0x7 <auth pap>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0x8 <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfRej id=0x8 <auth pap>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0x9 <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfRej id=0x9 <auth pap>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0xa <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfRej id=0xa <auth pap>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0xb <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfRej id=0xb <auth pap>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0xc <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfRej id=0xc <auth pap>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0xd <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfRej id=0xd <auth pap>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0xe <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfRej id=0xe <auth pap>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP ConfReq id=0xf <auth pap> <magic 0x2a30ad66>]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP ConfRej id=0xf <auth pap>]
Feb  8 17:23:24 ecdesktop pppd[6235]: rcvd [LCP TermReq id=0x10]
Feb  8 17:23:24 ecdesktop pppd[6235]: sent [LCP TermAck id=0x10]
Feb  8 17:23:24 ecdesktop pptp[6241]: anon log[ctrlp_disp:pptp_ctrl.c:928]: Call disconnect notification received (call id 27907)
Feb  8 17:23:24 ecdesktop pptp[6241]: anon log[ctrlp_disp:pptp_ctrl.c:787]: Received Stop Control Connection Request.
Feb  8 17:23:24 ecdesktop pptp[6241]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 4 'Stop-Control-Connection-Reply' 
Feb  8 17:23:24 ecdesktop pptp[6241]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Feb  8 17:23:24 ecdesktop pptp[6241]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Feb  8 17:23:24 ecdesktop pptp[6241]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Feb  8 17:23:24 ecdesktop pppd[6235]: Script /usr/sbin/pptp 192.168.51.1 --nolaunchpppd finished (pid 6237), status = 0x0
Feb  8 17:23:24 ecdesktop pppd[6235]: Modem hangup
Feb  8 17:23:24 ecdesktop pppd[6235]: Connection terminated.
Feb  8 17:23:24 ecdesktop pppd[6235]: Exit.
Feb  8 17:23:26 ecdesktop dhclient: DHCPREQUEST of <null address> on eth0 to 10.39.136.1 port 67
Feb  8 17:23:26 ecdesktop dhclient: DHCPACK of 10.39.136.37 from 10.39.136.1
Feb  8 17:23:26 ecdesktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Feb  8 17:23:26 ecdesktop dhclient: bound to 10.39.136.37 -- renewal in 294 seconds.
Feb  8 17:23:34 ecdesktop NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'. 
Feb  8 17:23:34 ecdesktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5. 
Feb  8 17:23:34 ecdesktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6. 
Feb  8 17:23:34 ecdesktop NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'lanck' because service was 6.

---

### Post by sun811 on 2009-02-10
Sorry that nobody responded to my query. Still the problem proved to be not a difficult one. For those who have same kind of trouble and are still in search of a solution I will outline what was wrong and what should be done to fix the issue.
First of all as it turned out Ubuntu 8.04 network-manager-pptp does not support PAP authentication and therefore should be called buggy and thrown to the trash bin. There are several other approaches. One is to use pptp-config, but as I was offline and it had many dependencies I had to opt for manual configuration. 
Google for pptp ubuntu vpn manual and you will find the necessary steps. Still for me such recipies were only a help not a remedy. I had to modify pap-secrets file instead of chap-secrets, reject all encryption and compression. Also routes had to be changed when the PPTP connection came over.

---

