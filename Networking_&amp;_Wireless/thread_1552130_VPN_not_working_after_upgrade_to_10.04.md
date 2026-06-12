---
title: "VPN not working after upgrade to 10.04"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by CptBlack91 on 2010-08-13
I've just upgraded from 9.10 to 10.04 and I cannot connect to my university's VPN now.  The error says "Connection attempt timed out". Hopefully the following log might be useful in solving this.

I've searched but cannot find anything useful. I've re-entered the details to make sure they're correct, reinstalled the pptp package.

Cheers,
Chris

```
chris@chris-desktop:~$ tail -f /var/log/syslog
Aug 13 12:52:21 chris-desktop pppd[3321]: Child process /usr/sbin/pptp student-vpn.bris.ac.uk --nolaunchpppd --logstring nm-pptp-service-3279 (pid 3322) terminated with signal 15
Aug 13 12:52:21 chris-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Aug 13 12:52:21 chris-desktop pppd[3321]: Connection terminated.
Aug 13 12:52:21 chris-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 13 12:52:21 chris-desktop pptp[3323]: nm-pptp-service-3279 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Aug 13 12:52:21 chris-desktop pptp[3323]: nm-pptp-service-3279 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Aug 13 12:52:21 chris-desktop pppd[3321]: Exit.
Aug 13 12:52:21 chris-desktop pptp[3331]: nm-pptp-service-3279 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Aug 13 12:52:21 chris-desktop pptp[3331]: nm-pptp-service-3279 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Aug 13 12:52:21 chris-desktop pptp[3331]: nm-pptp-service-3279 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Aug 13 12:52:34 chris-desktop NetworkManager: <debug> [1281700354.002882] ensure_killed(): waiting for vpn service pid 3279 to exit
Aug 13 12:52:34 chris-desktop NetworkManager: <debug> [1281700354.002965] ensure_killed(): vpn service pid 3279 cleaned up
Aug 13 12:52:34 chris-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Aug 13 12:52:34 chris-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 3396
Aug 13 12:52:34 chris-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Aug 13 12:52:34 chris-desktop pppd[3398]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug 13 12:52:34 chris-desktop NetworkManager: <info>  VPN plugin state changed: 3
Aug 13 12:52:34 chris-desktop pppd[3398]: pppd 2.4.5 started by root, uid 0
Aug 13 12:52:34 chris-desktop pppd[3398]: Using interface ppp0
Aug 13 12:52:34 chris-desktop pppd[3398]: Connect: ppp0 <--> /dev/pts/2
Aug 13 12:52:34 chris-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 13 12:52:34 chris-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Aug 13 12:52:34 chris-desktop NetworkManager: <info>  VPN connection 'Bristol VPN' (Connect) reply received.
Aug 13 12:52:39 chris-desktop pptp[3403]: nm-pptp-service-3396 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Aug 13 12:52:39 chris-desktop pptp[3409]: nm-pptp-service-3396 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Aug 13 12:52:39 chris-desktop pptp[3409]: nm-pptp-service-3396 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Aug 13 12:52:39 chris-desktop pptp[3409]: nm-pptp-service-3396 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Aug 13 12:52:40 chris-desktop pptp[3409]: nm-pptp-service-3396 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Aug 13 12:52:40 chris-desktop pptp[3409]: nm-pptp-service-3396 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Aug 13 12:52:40 chris-desktop pptp[3409]: nm-pptp-service-3396 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 7168).
Aug 13 12:52:41 chris-desktop pppd[3398]: CHAP authentication succeeded
Aug 13 12:52:41 chris-desktop pppd[3398]: MPPE 128-bit stateless compression enabled
Aug 13 12:52:41 chris-desktop pppd[3398]: Cannot determine ethernet address for proxy ARP
Aug 13 12:52:41 chris-desktop pppd[3398]: local  IP address 172.21.134.40
Aug 13 12:52:41 chris-desktop pppd[3398]: remote IP address 172.21.135.231
Aug 13 12:52:41 chris-desktop pppd[3398]: primary   DNS address 137.222.253.83
Aug 13 12:52:41 chris-desktop pppd[3398]: secondary DNS address 137.222.253.84
Aug 13 12:53:14 chris-desktop NetworkManager: <info>  VPN connection 'Bristol VPN' (IP Config Get) timeout exceeded.
Aug 13 12:53:27 chris-desktop pppd[3398]: Terminating on signal 15
Aug 13 12:53:27 chris-desktop pppd[3398]: Connect time 0.8 minutes.
Aug 13 12:53:27 chris-desktop pppd[3398]: Sent 0 bytes, received 0 bytes.
Aug 13 12:53:27 chris-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Aug 13 12:53:27 chris-desktop pppd[3398]: MPPE disabled
Aug 13 12:53:27 chris-desktop pppd[3398]: Child process /usr/sbin/pptp student-vpn.bris.ac.uk --nolaunchpppd --logstring nm-pptp-service-3396 (pid 3399) terminated with signal 15
Aug 13 12:53:27 chris-desktop pppd[3398]: Connection terminated.
Aug 13 12:53:27 chris-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 13 12:53:27 chris-desktop pptp[3403]: nm-pptp-service-3396 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Aug 13 12:53:27 chris-desktop pptp[3403]: nm-pptp-service-3396 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Aug 13 12:53:27 chris-desktop pppd[3398]: Exit.
Aug 13 12:53:27 chris-desktop pptp[3409]: nm-pptp-service-3396 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Aug 13 12:53:27 chris-desktop pptp[3409]: nm-pptp-service-3396 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Aug 13 12:53:27 chris-desktop pptp[3409]: nm-pptp-service-3396 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)

```

---

### Post by CptBlack91 on 2010-08-15
Can anyone shed some light on this?
I'm quite desperate to access my university network to continue some work.

Alternatively, is it possible to roll back to the 9.10 distro so the vpn works correctly again?

---

### Post by CptBlack91 on 2010-08-16
Can anyone point in the direction where I could get more help?
I'm desperate to get this working as soon as possible

---

### Post by CptBlack91 on 2010-08-25
Anyone?

---

### Post by rootyourbrain on 2013-04-15
> **CptBlack91 said:**
> Anyone?

Did you ever get this to work?

---

### Post by Iowan on 2013-04-15
Old thread - closed.

---

