---
title: "Vpn microsoft ppp ¡¡ problem !!"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by mr.ip on 2009-08-20
Hi everybody,


I have a problem to connect to my company's vpn. I did some research and followed several howtos. I have googled for hours. My actual configuration is:
******************************************************************************
Configuration (network manager)

Gateway *******
User: DOMAIN\user
password: blank
Advanced:
PAP and EAP are disabled and MPPE enabled.
******************************************************************************
After clicking on my vpn connection on Network manager and typing my password if I look in /var/log/syslog I see this:

Aug 20 11:51:02 dell NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Aug 20 11:51:02 dell NetworkManager: <info> VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 13396 
Aug 20 11:51:02 dell NetworkManager: <info> VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Aug 20 11:51:07 dell NetworkManager: <info>  VPN plugin state changed: 3 
Aug 20 11:51:07 dell NetworkManager: <info>  VPN connection 'Conexión VPN 1' (Connect) reply received. 
Aug 20 11:51:07 dell pppd[13399]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug 20 11:51:07 dell pppd[13399]: pppd 2.4.5 started by root, uid 0
Aug 20 11:51:07 dell pppd[13399]: Using interface ppp0
Aug 20 11:51:07 dell pppd[13399]: Connect: ppp0 <--> /dev/pts/5
Aug 20 11:51:07 dell pptp[13401]: nm-pptp-service-13396 log[mainptp.c:314]: The synchronous pptp option is NOT activated 
Aug 20 11:51:07 dell pptp[13411]: nm-pptp-service-13396 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Aug 20 11:51:07 dell pptp[13411]: nm-pptp-service-13396 log[ctrlp_dispptp_ctrl.c:739]: Received Start Control Connection Reply
Aug 20 11:51:07 dell pptp[13411]: nm-pptp-service-13396 log[ctrlp_dispptp_ctrl.c:773]: Client connection established.
Aug 20 11:51:08 dell pptp[13411]: nm-pptp-service-13396 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Aug 20 11:51:08 dell pptp[13411]: nm-pptp-service-13396 log[ctrlp_dispptp_ctrl.c:858]: Received Outgoing Call Reply.
Aug 20 11:51:08 dell pptp[13411]: nm-pptp-service-13396 log[ctrlp_dispptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 32812). 
**Aug 20 11:51:08 dell pptp[13401]: nm-pptp-service-13396 warn[decaps_greptp_gre.c:331]: short read (-1): Protocol not available**
Aug 20 11:51:08 dell pptp[13411]: nm-pptp-service-13396 log[callmgr_mainptp_callmgr.c:234]: Closing connection (unhandled)
Aug 20 11:51:08 dell pppd[13399]: Modem hangup
Aug 20 11:51:08 dell pptp[13411]: nm-pptp-service-13396 log[ctrlp_repptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Aug 20 11:51:08 dell pptp[13411]: nm-pptp-service-13396 log[call_callbackptp_callmgr.c:79]: Closing connection (call state)
Aug 20 11:51:08 dell NetworkManager: <info>  VPN plugin failed: 1 
Aug 20 11:51:08 dell pppd[13399]: Connection terminated.
Aug 20 11:51:08 dell NetworkManager: <info>  VPN plugin failed: 1 
Aug 20 11:51:08 dell pppd[13399]: Exit.
Aug 20 11:51:08 dell NetworkManager: <info>  VPN plugin failed: 1 
Aug 20 11:51:08 dell NetworkManager: <info>  VPN plugin state changed: 6 
Aug 20 11:51:08 dell NetworkManager: <info>  VPN plugin state change reason: 0 
Aug 20 11:51:08 dell NetworkManager: <WARN> connection_state_changed(): Could not process the request because no VPN connection was active. 
Aug 20 11:51:08 dell NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Aug 20 11:51:21 dell NetworkManager: <debug> [1250761881.002319] ensure_killed(): waiting for vpn service pid 13396 to exit 
Aug 20 11:51:21 dell NetworkManager: <debug> [1250761881.002389] ensure_killed(): vpn service pid 13396 cleaned up 

I did some research about this line **Aug 20 11:51:08 dell pptp[13401]: nm-pptp-service-13396 warn[decaps_greptp_gre.c:331]: short read (-1): Protocol not available**
and I found this [http://pptpclient.sourceforge.net/howto ... ead_eproto]("http://pptpclient.sourceforge.net/howto-diagnosis.phtml#read_eproto")
*************************************************************************************************************************************************************************************************************************************************************
Protocol not available
Symptom: the following messages appear before the tunnel is established:

log[pptp_dispatch_ctrl_packetptp_ctrl.c:580]: Client connection established.
log[pptp_dispatch_ctrl_packetptp_ctrl.c:708]: Outgoing call established (call ID 0, peer's call ID 0).
log[decaps_greptp_gre.c:215]: short read (4294967295): Protocol not available
log[callmgr_mainptp_callmgr.c:245]: Closing connection
log[pptp_conn_closeptp_ctrl.c:307]: Closing PPTP connection
log[call_callbackptp_callmgr.c:88]: Closing connection

Diagnosis: usually caused by the client not binding to the GRE socket early enough during the connection sequence. The first GRE packet from the server causes an ICMP protocol unreachable reply. This happens more frequently on high speed connections.

Workaround: load the ip_gre module. This prevents the ICMP protocol unreachable reply from being generated.

# modprobe ip_gre

Solution: upgrade to pptp-linux 1.2.0, which binds the GRE socket prior to calling the server. Loading the ip_gre module should not be needed.

*************************************************************************************************************************************************************************************************************************************************************
My pptp-linux version is: 1.7.2-1. I have tried this solution an even including the module ip_gre in /etc/modules and restarting but the problem persists. The module loads without problem and if I do and ifconfig -a I can see it. 

I have not firewalls and I'm not behind a router. I would appreciate very much if someone could help me to solve this problem. I don't want to switch back to Windows Xp and I don't want to hear my boss kidding me saying that Linux is ********, 

Regards,
Mr.Ip

---

