---
title: "OpenVPN disconnects"
date: 2012-10-07
forum: Networking &amp; Wireless
---

### Post by Heisenborg on 2012-10-07
OS Ubuntu 12.04 32-bit with the latest fixes to date.

I've long had this VPN set up. It had been working flawlessly until about a week ago when it started to unexpectedly disconnect.

I use Unity and NetworkManager. I click on NM -> VPN Connections -> <VPN Connection Name> and it connects without fail every time. However, 120 seconds in the connection ping stops responding from the other end (and all other type of traffic through this VPN channel stops as well). After another 120 seconds the connection is dropped.

_The exact same config works flawlessly on a Windows box._

Here's the config:

```

client
dev tun
proto udp
remote aa.bb.ccc.ddd 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert secretuser.crt
key secretuser.key
ns-cert-type server
tls-auth ta.key 1
comp-lzo
verb 7
```

And here's a transcript of a session:

```

Oct  7 10:39:23 black NetworkManager[1153]: <info> Starting VPN service 'openvpn'...
Oct  7 10:39:23 black NetworkManager[1153]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 31152
Oct  7 10:39:23 black NetworkManager[1153]: <info> VPN service 'openvpn' appeared; activating connections
Oct  7 10:39:23 black NetworkManager[1153]: <info> VPN plugin state changed: starting (3)
Oct  7 10:39:23 black NetworkManager[1153]: <info> VPN connection 'SecretVPN' (Connect) reply received.
Oct  7 10:39:23 black nm-openvpn[31155]: OpenVPN 2.2.1 i686-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Mar 30 2012
Oct  7 10:39:23 black nm-openvpn[31155]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Oct  7 10:39:23 black nm-openvpn[31155]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Oct  7 10:39:23 black nm-openvpn[31155]: Control Channel Authentication: using '/home/secretuser/Auth/SecretVPN/ta.key' as a OpenVPN static key file
Oct  7 10:39:23 black nm-openvpn[31155]: LZO compression initialized
Oct  7 10:39:23 black nm-openvpn[31155]: UDPv4 link local: [undef]
Oct  7 10:39:23 black nm-openvpn[31155]: UDPv4 link remote: [AF_INET]aa.bb.ccc.ddd:1194
Oct  7 10:39:24 black nm-openvpn[31155]: [server] Peer Connection Initiated with [AF_INET]aa.bb.ccc.ddd:1194
Oct  7 10:39:26 black NetworkManager[1153]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Oct  7 10:39:26 black NetworkManager[1153]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Oct  7 10:39:26 black nm-openvpn[31155]: TUN/TAP device tun0 opened
Oct  7 10:39:26 black nm-openvpn[31155]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper tun0 1500 1542 eee.ff.gg.hh eee.ff.gg.ii init
Oct  7 10:39:26 black NetworkManager[1153]: <info> VPN connection 'SecretVPN' (IP Config Get) reply received.
Oct  7 10:39:26 black NetworkManager[1153]: <info> VPN Gateway: aa.bb.ccc.ddd
Oct  7 10:39:26 black NetworkManager[1153]: <info> Internal Gateway: eee.ff.gg.ii
Oct  7 10:39:26 black NetworkManager[1153]: <info> Tunnel Device: tun0
Oct  7 10:39:26 black NetworkManager[1153]: <info> Internal IP4 Address: eee.ff.gg.hh
Oct  7 10:39:26 black NetworkManager[1153]: <info> Internal IP4 Prefix: 32
Oct  7 10:39:26 black NetworkManager[1153]: <info> Internal IP4 Point-to-Point Address: eee.ff.gg.ii
Oct  7 10:39:26 black NetworkManager[1153]: <info> Maximum Segment Size (MSS): 0
Oct  7 10:39:26 black NetworkManager[1153]: <info> Static Route: jjj.kkk.ll.0/24   Next Hop: jjj.kkk.ll.0
Oct  7 10:39:26 black NetworkManager[1153]: <info> Static Route: jjj.kkk.mm.0/24   Next Hop: jjj.kkk.mm.0
Oct  7 10:39:26 black NetworkManager[1153]: <info> Static Route: eee.ff.gg.0/24   Next Hop: eee.ff.gg.0
Oct  7 10:39:26 black NetworkManager[1153]: <info> Forbid Default Route: no
Oct  7 10:39:26 black NetworkManager[1153]: <info> Internal IP4 DNS: jjj.kkk.ll.253
Oct  7 10:39:26 black NetworkManager[1153]: <info> DNS Domain: '(none)'
Oct  7 10:39:26 black nm-openvpn[31155]: Initialization Sequence Completed
Oct  7 10:39:27 black NetworkManager[1153]: <info> (tun0): writing resolv.conf to /sbin/resolvconf
Oct  7 10:39:28 black NetworkManager[1153]: <info> VPN connection 'SecretVPN' (IP Config Get) complete.
Oct  7 10:39:28 black NetworkManager[1153]: <info> Policy set 'station-66' (wlan0) as default for IPv4 routing and DNS.
Oct  7 10:39:28 black NetworkManager[1153]: <info> VPN plugin state changed: started (4)
Oct  7 10:39:28 black dbus[1105]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct  7 10:39:28 black dbus[1105]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'

Oct  7 10:43:21 black nm-openvpn[31155]: [server] Inactivity timeout (--ping-restart), restarting
Oct  7 10:43:21 black nm-openvpn[31155]: SIGUSR1[soft,ping-restart] received, process restarting
Oct  7 10:43:23 black nm-openvpn[31155]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Oct  7 10:43:23 black nm-openvpn[31155]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Oct  7 10:43:23 black nm-openvpn[31155]: Re-using SSL/TLS context
Oct  7 10:43:23 black nm-openvpn[31155]: LZO compression initialized
Oct  7 10:43:23 black nm-openvpn[31155]: UDPv4 link local: [undef]
Oct  7 10:43:23 black nm-openvpn[31155]: UDPv4 link remote: [AF_INET]aa.bb.ccc.ddd:1194
Oct  7 10:43:24 black nm-openvpn[31155]: [server] Peer Connection Initiated with [AF_INET]aa.bb.ccc.ddd:1194
Oct  7 10:43:27 black nm-openvpn[31155]: Preserving previous TUN/TAP instance: tun0
Oct  7 10:43:27 black nm-openvpn[31155]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper tun0 1500 1542 eee.ff.gg.hh eee.ff.gg.ii restart
Oct  7 10:43:27 black NetworkManager[1153]: <warn> VPN plugin failed: 2
Oct  7 10:43:27 black nm-openvpn[31155]: WARNING: Failed running command (--up/--down): external program exited with error status: 1
Oct  7 10:43:27 black nm-openvpn[31155]: Exiting
Oct  7 10:43:27 black avahi-daemon[1129]: Withdrawing workstation service for tun0.
Oct  7 10:43:27 black NetworkManager[1153]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Oct  7 10:43:27 black NetworkManager[1153]: <warn> VPN plugin failed: 1
Oct  7 10:43:27 black NetworkManager[1153]: <info> VPN plugin state changed: stopped (6)
Oct  7 10:43:27 black NetworkManager[1153]: <info> VPN plugin state change reason: 0
Oct  7 10:43:27 black NetworkManager[1153]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Oct  7 10:43:27 black NetworkManager[1153]: <warn> (9) failed to find interface name for index
Oct  7 10:43:27 black NetworkManager[1153]: nm_system_iface_flush_routes: assertion `iface != NULL' failed
Oct  7 10:43:27 black NetworkManager[1153]: <warn> (9) failed to find interface name for index
Oct  7 10:43:27 black NetworkManager[1153]: <info> (tun0): writing resolv.conf to /sbin/resolvconf
Oct  7 10:43:28 black NetworkManager[1153]: <info> Policy set 'station-66' (wlan0) as default for IPv4 routing and DNS.
Oct  7 10:43:28 black dbus[1105]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct  7 10:43:28 black dbus[1105]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  7 10:43:33 black NetworkManager[1153]: <info> VPN service 'openvpn' disappeared

```

I have no access to the server side.

I'd appreciate any useful comments.

---

