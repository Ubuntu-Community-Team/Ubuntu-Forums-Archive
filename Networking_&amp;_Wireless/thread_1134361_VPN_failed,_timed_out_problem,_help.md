---
title: "VPN failed, timed out problem, help"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by pinakas on 2009-04-23
hello from Greeece,

I try to setup a pptp vpn account on ubuntu 9.04

I have install the network manager and network manager pptp

I tried the setting of my vpn provifer (hotspotyvpn.com) and always I get the error: Failed, connection timed out.

I tried to unistall the managers, install them again - change different settings in encryption etc - try another VPN, but nothing worked

See the log of the connection, where is the problem ? Please help
I work on the problem for 5 days with no solution

eleftherios@eleftherios-laptop:~$ tail -f /var/log/syslog
Apr 23 23:53:00 eleftherios-laptop pptp[543]: nm-pptp-service-538 log[decaps_gre:pptp_gre.c:414]: buffering packet 6 (expecting 5, lost or reordered)
Apr 23 23:53:00 eleftherios-laptop pptp[543]: nm-pptp-service-538 log[decaps_gre:pptp_gre.c:414]: buffering packet 7 (expecting 5, lost or reordered)
Apr 23 23:53:00 eleftherios-laptop pppd[541]: CHAP authentication succeeded
Apr 23 23:53:31 eleftherios-laptop pptp[553]: nm-pptp-service-538 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Apr 23 23:53:31 eleftherios-laptop pptp[553]: nm-pptp-service-538 log[callmgr_main:pptp_callmgr.c:258]: Closing connection (shutdown)
Apr 23 23:53:31 eleftherios-laptop pptp[553]: nm-pptp-service-538 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Apr 23 23:53:31 eleftherios-laptop pptp[553]: nm-pptp-service-538 log[pptp_read_some:pptp_ctrl.c:544]: read returned zero, peer has closed
Apr 23 23:53:31 eleftherios-laptop pptp[553]: nm-pptp-service-538 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Apr 23 23:53:35 eleftherios-laptop NetworkManager: <info>  VPN connection 'VPN connection 1' (IP Config Get) timeout exceeded. 
Apr 23 23:53:35 eleftherios-laptop NetworkManager: <info>  Policy set 'Auto LFN' (eth1) as default for routing and DNS. 
Apr 23 23:53:47 eleftherios-laptop NetworkManager: <debug> [1240520027.002756] ensure_killed(): waiting for vpn service pid 538 to exit 
Apr 23 23:53:47 eleftherios-laptop NetworkManager: <debug> [1240520027.003042] ensure_killed(): vpn service pid 538 cleaned up

---

### Post by tellytart on 2009-08-23
I've just installed this, and having the same problems. I can't connect to my VPN server (Microsoft PPTP). I get the same timeout error.
 
I can connect to the VPN server happily with my iPhone and my Windows Vista and Windows 7 based laptops, just not Ubuntu.

---

