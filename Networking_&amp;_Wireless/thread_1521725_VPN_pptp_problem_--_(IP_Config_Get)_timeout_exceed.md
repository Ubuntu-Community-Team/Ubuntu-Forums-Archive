---
title: "VPN pptp problem -- (IP Config Get) timeout exceeded"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by d4y on 2010-07-01
Hi!

I'm trying to configure internet access using KDE network manager. Added new VPN connection, set gateway and other options but connection breaks. Here is /var/log/daemon.log
```

Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 1761
Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  VPN plugin state changed: 1
Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  VPN plugin state changed: 3
Jul  1 17:35:22 dvinokurov-desktop NetworkManager: <info>  VPN connection 'foovpn' (Connect) reply received.
Jul  1 17:35:22 dvinokurov-desktop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul  1 17:35:22 dvinokurov-desktop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jul  1 17:35:22 dvinokurov-desktop pptp[1766]: nm-pptp-service-1761 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jul  1 17:35:22 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jul  1 17:35:22 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jul  1 17:35:22 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jul  1 17:35:23 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jul  1 17:35:23 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jul  1 17:35:23 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 143).
Jul  1 17:36:02 dvinokurov-desktop NetworkManager: <info>  VPN connection 'foovpn' (IP Config Get) timeout exceeded.
Jul  1 17:36:02 dvinokurov-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jul  1 17:36:02 dvinokurov-desktop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jul  1 17:36:02 dvinokurov-desktop pptp[1766]: nm-pptp-service-1761 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jul  1 17:36:02 dvinokurov-desktop pptp[1766]: nm-pptp-service-1761 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jul  1 17:36:02 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jul  1 17:36:02 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jul  1 17:36:02 dvinokurov-desktop pptp[1773]: nm-pptp-service-1761 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)

```As I understand the main problem is in "(IP Config Get) timeout exceeded". Could anybody suggest a way to solve this problem?

Thanks

---

### Post by Iowan on 2010-07-01
Duplicate: [http://ubuntuforums.org/showthread.php?t=1521723]("http://ubuntuforums.org/showthread.php?t=1521723")

---

