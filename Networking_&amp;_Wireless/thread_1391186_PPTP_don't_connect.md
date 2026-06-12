---
title: "PPTP don't connect"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by Eps on 2010-01-26
Hi,

Kubuntu 9.10. Try to establish PPTP VPN to office and it fails.

daemon.log:

```
Jan 26 21:18:51 ubu-desk NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jan 26 21:18:51 ubu-desk NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 7575
Jan 26 21:18:51 ubu-desk NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jan 26 21:18:51 ubu-desk NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf
Jan 26 21:18:51 ubu-desk NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 26 21:18:51 ubu-desk NetworkManager: <info>  VPN plugin state changed: 3
Jan 26 21:18:51 ubu-desk NetworkManager: <info>  VPN connection 'TLG' (Connect) reply received.
Jan 26 21:18:51 ubu-desk NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 26 21:18:51 ubu-desk NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan 26 21:18:51 ubu-desk pptp[7580]: nm-pptp-service-7575 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan 26 21:18:51 ubu-desk pptp[7586]: nm-pptp-service-7575 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan 26 21:18:51 ubu-desk pptp[7586]: nm-pptp-service-7575 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan 26 21:18:51 ubu-desk pptp[7586]: nm-pptp-service-7575 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan 26 21:18:52 ubu-desk pptp[7586]: nm-pptp-service-7575 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan 26 21:18:52 ubu-desk pptp[7586]: nm-pptp-service-7575 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan 26 21:18:52 ubu-desk pptp[7586]: nm-pptp-service-7575 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 76).
Jan 26 21:19:28 ubu-desk NetworkManager: <info>  VPN plugin failed: 1
Jan 26 21:19:28 ubu-desk NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 26 21:19:28 ubu-desk pptp[7580]: nm-pptp-service-7575 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Jan 26 21:19:28 ubu-desk pptp[7580]: nm-pptp-service-7575 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Jan 26 21:19:28 ubu-desk pptp[7586]: nm-pptp-service-7575 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Jan 26 21:19:28 ubu-desk pptp[7586]: nm-pptp-service-7575 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Jan 26 21:19:28 ubu-desk pptp[7586]: nm-pptp-service-7575 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Jan 26 21:19:28 ubu-desk NetworkManager: <info>  VPN plugin failed: 1
Jan 26 21:19:28 ubu-desk NetworkManager: <info>  VPN plugin failed: 1
Jan 26 21:19:28 ubu-desk NetworkManager: <info>  VPN plugin state changed: 6
Jan 26 21:19:28 ubu-desk NetworkManager: <info>  VPN plugin state change reason: 0
Jan 26 21:19:28 ubu-desk NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jan 26 21:19:28 ubu-desk NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf
Jan 26 21:19:28 ubu-desk NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jan 26 21:19:41 ubu-desk NetworkManager: <debug> [1264533581.002343] ensure_killed(): waiting for vpn service pid 7575 to exit
Jan 26 21:19:41 ubu-desk NetworkManager: <debug> [1264533581.002585] ensure_killed(): vpn service pid 7575 cleaned up
```
auth.log:

```
an 26 21:20:58 ubu-desk dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.25" (uid=1000 pid=1848 comm="kdeinit4: plasma-desktop [kdeinit]") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.777" (uid=0 pid=7672 comm="/usr/sbin/packagekitd))
```network-manager-pptp in installed.

Any ideas what cause this fail?

Thanks.

Eps

---

