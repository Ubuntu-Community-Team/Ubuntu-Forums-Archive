---
title: "Connecting to Microsoft VPN - MPPE negotiation failing"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by dwightus on 2009-04-27
I've been struggling over the past week or so trying to get a connection from a Lenovo S10 notebook running Jaunty (9.04) to a Microsoft VPN at my workplace.

I am still fairly new at this so I apologise for any obvious moments of stupidity :P

I installed network-manager-pptp and pptp-linux without issue and then configured a new connection to try and match the following windows configuration (from XP).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=111475&stc=1&d=1240884763[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=111477&stc=1&d=1240885054[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=111476&stc=1&d=1240885054[/IMG]

This all seems to be pretty straightforward, however any time I attempt to connect to the VPN I receive a 'VPN Connection failed' alert.

The following is the output that I've pulled from /var/log/messages:

```

Apr 28 10:03:46 sciss10oem pppd[4156]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Apr 28 10:03:46 sciss10oem pppd[4156]: pppd 2.4.5 started by root, uid 0
Apr 28 10:03:46 sciss10oem pppd[4156]: Using interface ppp0
Apr 28 10:03:46 sciss10oem pppd[4156]: Connect: ppp0 <--> /dev/pts/3
Apr 28 10:03:47 sciss10oem pppd[4156]: CHAP authentication succeeded
Apr 28 10:03:47 sciss10oem pppd[4156]: Connection terminated.
Apr 28 10:03:47 sciss10oem pppd[4156]: Exit.
```And from /var/log/syslog
```
Apr 28 10:03:37 sciss10oem NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Apr 28 10:03:37 sciss10oem NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 4153 
Apr 28 10:03:37 sciss10oem NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Apr 28 10:03:37 sciss10oem NetworkManager: <info>  VPN plugin state changed: 1 
Apr 28 10:03:46 sciss10oem NetworkManager: <info>  VPN plugin state changed: 3 
Apr 28 10:03:46 sciss10oem NetworkManager: <info>  VPN connection 'VPN' (Connect) reply received. 
Apr 28 10:03:46 sciss10oem pppd[4156]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Apr 28 10:03:46 sciss10oem pppd[4156]: pppd 2.4.5 started by root, uid 0
Apr 28 10:03:46 sciss10oem pppd[4156]: Using interface ppp0
Apr 28 10:03:46 sciss10oem pppd[4156]: Connect: ppp0 <--> /dev/pts/3
Apr 28 10:03:46 sciss10oem pptp[4159]: nm-pptp-service-4153 log[main:pptp.c:314]: The synchronous pptp option is NOT activated 
Apr 28 10:03:46 sciss10oem pptp[4168]: nm-pptp-service-4153 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Apr 28 10:03:46 sciss10oem pptp[4168]: nm-pptp-service-4153 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Apr 28 10:03:46 sciss10oem pptp[4168]: nm-pptp-service-4153 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Apr 28 10:03:47 sciss10oem pptp[4168]: nm-pptp-service-4153 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Apr 28 10:03:47 sciss10oem pptp[4168]: nm-pptp-service-4153 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Apr 28 10:03:47 sciss10oem pptp[4168]: nm-pptp-service-4153 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 0). 
Apr 28 10:03:47 sciss10oem pppd[4156]: CHAP authentication succeeded
Apr 28 10:03:47 sciss10oem pppd[4156]: MPPE required but peer negotiation failed
Apr 28 10:03:47 sciss10oem pppd[4156]: Connection terminated.
Apr 28 10:03:47 sciss10oem NetworkManager: <info>  VPN plugin failed: 1 
Apr 28 10:03:47 sciss10oem pptp[4159]: nm-pptp-service-4153 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Apr 28 10:03:47 sciss10oem pptp[4159]: nm-pptp-service-4153 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Apr 28 10:03:47 sciss10oem pptp[4168]: nm-pptp-service-4153 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Apr 28 10:03:47 sciss10oem pptp[4168]: nm-pptp-service-4153 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Apr 28 10:03:47 sciss10oem pptp[4168]: nm-pptp-service-4153 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Apr 28 10:03:47 sciss10oem pppd[4156]: Exit.
Apr 28 10:03:47 sciss10oem NetworkManager: <info>  VPN plugin state changed: 6 
Apr 28 10:03:47 sciss10oem NetworkManager: <info>  VPN plugin state change reason: 0 
Apr 28 10:03:47 sciss10oem NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Apr 28 10:03:47 sciss10oem NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Apr 28 10:04:00 sciss10oem NetworkManager: <debug> [1240884240.002907] ensure_killed(): waiting for vpn service pid 4153 to exit 
Apr 28 10:04:00 sciss10oem NetworkManager: <debug> [1240884240.003276] ensure_killed(): vpn service pid 4153 cleaned up 

```The connection appears to authenticate okay but then disconnects after MPPE peer negotiation fails. I've tried setting MPPE to allow stateful encryption and to use any available MPPE type, but without success.

I can't find anything in NetworkManager regarding MCCP and am starting to wonder if that is related (as the working connection in Windows is using it).

Any suggestions would be greatly appreciated.

---

### Post by dwightus on 2009-04-27
Curiously enough, I am able to connect to another VPN with similar settings.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=111483&stc=1&d=1240887625[/IMG]

The above VPN connects without issue in my ubuntu install, using the same settings as set above for the original VPN connection, so obviously it's an issue with that VPN on some level. Now it's just a matter of trying to determine *where*.

---

### Post by dwightus on 2009-04-30
Is there an additional debugging mode or system log that I might be able to view to try and diagnose what it is about the MPPE negotiation that isn't doing what it should?

Any thoughts?

---

