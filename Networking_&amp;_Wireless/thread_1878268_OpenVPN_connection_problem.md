---
title: "OpenVPN connection problem"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by faflu on 2011-11-09
Hi,

I have a strange problem with establishing VPN network after an upgrade from 11.4 to 11.11. I'm using gnome network-manager
NM applet says it successfully established connection, but:
- I can't access remote network
- tun device is not visible in ifconfig, though it's enabled according to e.g.: firestarter.
- routing table doesn't contain any entries that would put the traffic to remote network
Here's the log:
```
Nov  9 19:17:27 f-desktop nm-openvpn[11125]: OpenVPN 2.2.0 i686-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Jul  4 2011
Nov  9 19:17:27 f-desktop nm-openvpn[11125]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Nov  9 19:17:27 f-desktop nm-openvpn[11125]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Nov  9 19:17:27 f-desktop nm-openvpn[11125]: WARNING: file '/home/michalf/vpn/michal.key' is group or others accessible
Nov  9 19:17:27 f-desktop nm-openvpn[11125]: Attempting to establish TCP connection with [AF_INET]remote.gw.address:1194 [nonblock]
Nov  9 19:17:28 f-desktop nm-openvpn[11125]: TCP connection established with [AF_INET]remote.gw.address:1194
Nov  9 19:17:28 f-desktop nm-openvpn[11125]: TCPv4_CLIENT link local: [undef]
Nov  9 19:17:28 f-desktop nm-openvpn[11125]: TCPv4_CLIENT link remote: [AF_INET]remote.gw.address:1194
Nov  9 19:17:31 f-desktop nm-openvpn[11125]: [server] Peer Connection Initiated with [AF_INET]remote.gw.address:1194
Nov  9 19:17:34 f-desktop nm-openvpn[11125]: TUN/TAP device tun0 opened
Nov  9 19:17:34 f-desktop nm-openvpn[11125]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper tun0 1500 1543 192.168.3.30 192.168.3.29 init
Nov  9 19:17:34 f-desktop kernel: [12765.623929] tun0: Disabled Privacy Extensions
Nov  9 19:17:34 f-desktop nm-openvpn[11125]: Initialization Sequence Completed
Nov  9 19:17:34 f-desktop NetworkManager[1169]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Nov  9 19:17:34 f-desktop NetworkManager[1169]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> VPN connection 'borg' (IP Config Get) reply received.
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> VPN Gateway: remote.gw.address
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> Internal Gateway: 192.168.3.29
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> Tunnel Device: tun0
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> Internal IP4 Address: 192.168.3.30
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> Internal IP4 Prefix: 32
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> Internal IP4 Point-to-Point Address: 192.168.3.29
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> Maximum Segment Size (MSS): 0
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> Static Route: 192.168.2.0/24   Next Hop: 192.168.2.0
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> Static Route: 129.1.1.0/24   Next Hop: 129.1.1.0
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> Static Route: 192.168.3.1/32   Next Hop: 192.168.3.1
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> Forbid Default Route: no
Nov  9 19:17:34 f-desktop NetworkManager[1169]: <info> DNS Domain: '(none)'
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <warn> Failed to add route Object not found
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <warn> Failed to add route Object not found
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <error> [1320862655.225013] [nm-system.c:136] nm_system_device_set_ip4_route(): (tun0): failed to set IPv4 route: Object not found
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <warn> Failed to add route Object not found
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <warn> Failed to add route Object not found
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <error> [1320862655.225168] [nm-system.c:136] nm_system_device_set_ip4_route(): (tun0): failed to set IPv4 route: Object not found
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <warn> Failed to add route Object not found
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <warn> Failed to add route Object not found
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <error> [1320862655.225320] [nm-system.c:136] nm_system_device_set_ip4_route(): (tun0): failed to set IPv4 route: Object not found
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <warn> (tun0): failed to change interface MTU
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <info> (tun0): writing resolv.conf to /sbin/resolvconf
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <info> VPN connection 'borg' (IP Config Get) complete.
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <warn> Failed to add route Object not found
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <warn> Failed to add route Object not found
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <error> [1320862655.264931] [nm-system.c:889] nm_system_replace_default_ip4_route_vpn(): (tun0): failed to set IPv4 default route (pass #2): -12
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <info> Policy set 'borg' (tun0) as default for IPv4 routing and DNS.
Nov  9 19:17:35 f-desktop NetworkManager[1169]: <info> VPN plugin state changed: 4
Nov  9 19:17:35 f-desktop dbus[1097]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov  9 19:17:35 f-desktop dbus[1097]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
```

Anyone can knows where to look for the solution?

---

