---
title: "traffic problemswith network-manager-openvpn via SOCKS Proxy, offered by SSH"
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by DomTomcat on 2011-10-08
Hi there,

I want to set up a VPN (oneiric, gnome) by connecting to a host. This works just fine.
But once I try to run it over a ssh -D tunnel, it doesn't work anymore.

I start the ssh proxy server:
ssh -vvv -D 9999 HOSTA

then I go to network-manager create a new OpenVPN connection, just like I do when connecting without a proxy. That is, I connect to HOSTB (same network as HOSTA) port 80, with TCP TAP LZO enabled.
Additionally, in the proxy tabs setting, I set the proxy to 127.0.0.1 and port 9999.

Connection is established successfully, but then connection stalls. No ping to any IPs outside the new local network (10.8.0.x). As if ssh traffic is tried to be routed over VPN, as well.

Is this approach possible in the first place ? if no, how can I perform VPN over a SSH tunnel with network-manager ? if yes, any ideas ?

output of ssh:
```

debug1: channel 3: new [dynamic-tcpip]
debug2: channel 3: pre_dynamic: have 0
debug2: channel 3: pre_dynamic: have 4
debug2: channel 3: decode socks5
debug2: channel 3: socks5 auth done
debug2: channel 3: pre_dynamic: need more
debug2: channel 3: pre_dynamic: have 0
debug2: channel 3: pre_dynamic: have 20
debug2: channel 3: decode socks5
debug2: channel 3: socks5 post auth
debug2: channel 3: dynamic request: socks5 host HOSTB port 80 command 1
debug2: channel 3: open confirm rwindow 2097152 rmax 3276

```

syslog, including manual disconnection:
```

Oct  8 18:15:01 domdesktop NetworkManager[1085]: <info> Starting VPN service 'openvpn'...
Oct  8 18:15:01 domdesktop NetworkManager[1085]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 4033
Oct  8 18:15:01 domdesktop NetworkManager[1085]: <info> VPN service 'openvpn' appeared; activating connections
Oct  8 18:15:01 domdesktop NetworkManager[1085]: <info> VPN plugin state changed: 3
Oct  8 18:15:01 domdesktop NetworkManager[1085]: <info> VPN connection 'HU Orion SOCKS5' (Connect) reply received.
Oct  8 18:15:01 domdesktop nm-openvpn[4036]: OpenVPN 2.2.0 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Jul  4 2011
Oct  8 18:15:01 domdesktop nm-openvpn[4036]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Oct  8 18:15:01 domdesktop nm-openvpn[4036]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Oct  8 18:15:01 domdesktop nm-openvpn[4036]: WARNING: file '/home/ruess/.ssh/hu-orion/rues_dm.key' is group or others accessible
Oct  8 18:15:01 domdesktop nm-openvpn[4036]: LZO compression initialized
Oct  8 18:15:01 domdesktop nm-openvpn[4036]: Attempting to establish TCP connection with [AF_INET]127.0.0.1:9999 [nonblock]
Oct  8 18:15:01 domdesktop nm-openvpn[4036]: TCP connection established with [AF_INET]127.0.0.1:9999
Oct  8 18:15:01 domdesktop nm-openvpn[4036]: TCPv4_CLIENT link local: [undef]
Oct  8 18:15:01 domdesktop nm-openvpn[4036]: TCPv4_CLIENT link remote: [AF_INET]127.0.0.1:9999
Oct  8 18:15:02 domdesktop nm-openvpn[4036]: [server] Peer Connection Initiated with [AF_INET]127.0.0.1:9999
Oct  8 18:15:04 domdesktop NetworkManager[1085]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tap0, iface: tap0)
Oct  8 18:15:04 domdesktop NetworkManager[1085]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tap0, iface: tap0): no ifupdown configuration found.
Oct  8 18:15:04 domdesktop nm-openvpn[4036]: TUN/TAP device tap0 opened
Oct  8 18:15:04 domdesktop nm-openvpn[4036]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper tap0 1500 1576 10.8.0.52 255.255.255.0 init
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <warn> /sys/devices/virtual/net/tap0: couldn't determine device driver; ignoring...
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> VPN connection 'HU Orion SOCKS5' (IP Config Get) reply received.
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> VPN Gateway: 127.0.0.1
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> Internal Gateway: 10.8.0.1
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> Tunnel Device: tap0
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> Internal IP4 Address: 10.8.0.52
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> Internal IP4 Prefix: 24
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> Internal IP4 Point-to-Point Address: 0.0.0.0
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> Maximum Segment Size (MSS): 0
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> Forbid Default Route: no
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> Internal IP4 DNS: 208.67.222.222
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> Internal IP4 DNS: 208.67.220.220
Oct  8 18:15:04 domdesktop NetworkManager[1085]: <info> DNS Domain: '(none)'
Oct  8 18:15:04 domdesktop nm-openvpn[4036]: Initialization Sequence Completed
Oct  8 18:15:04 domdesktop avahi-daemon[1083]: Joining mDNS multicast group on interface tap0.IPv4 with address 10.8.0.52.
Oct  8 18:15:04 domdesktop avahi-daemon[1083]: New relevant interface tap0.IPv4 for mDNS.
Oct  8 18:15:04 domdesktop avahi-daemon[1083]: Registering new address record for 10.8.0.52 on tap0.IPv4.
Oct  8 18:15:05 domdesktop NetworkManager[1085]: <info> VPN connection 'HU Orion SOCKS5' (IP Config Get) complete.
Oct  8 18:15:05 domdesktop NetworkManager[1085]: <info> Policy set 'HU Orion SOCKS5' (tap0) as default for IPv4 routing and DNS.
Oct  8 18:15:05 domdesktop NetworkManager[1085]: <info> VPN plugin state changed: 4
Oct  8 18:15:05 domdesktop dbus[1072]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Oct  8 18:15:05 domdesktop dbus[1072]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  8 18:15:06 domdesktop avahi-daemon[1083]: Joining mDNS multicast group on interface tap0.IPv6 with address fe80::406c:97ff:fe68:967a.
Oct  8 18:15:06 domdesktop avahi-daemon[1083]: New relevant interface tap0.IPv6 for mDNS.
Oct  8 18:15:06 domdesktop avahi-daemon[1083]: Registering new address record for fe80::406c:97ff:fe68:967a on tap0.*.
Oct  8 18:15:07 domdesktop avahi-daemon[1083]: Interface tap0.IPv6 no longer relevant for mDNS.
Oct  8 18:15:07 domdesktop avahi-daemon[1083]: Leaving mDNS multicast group on interface tap0.IPv6 with address fe80::406c:97ff:fe68:967a.
Oct  8 18:15:07 domdesktop avahi-daemon[1083]: Interface tap0.IPv4 no longer relevant for mDNS.
Oct  8 18:15:07 domdesktop avahi-daemon[1083]: Leaving mDNS multicast group on interface tap0.IPv4 with address 10.8.0.52.
Oct  8 18:15:07 domdesktop avahi-daemon[1083]: Withdrawing address record for fe80::406c:97ff:fe68:967a on tap0.
Oct  8 18:15:07 domdesktop avahi-daemon[1083]: Withdrawing address record for 10.8.0.52 on tap0.
Oct  8 18:15:07 domdesktop NetworkManager[1085]: nm_system_iface_flush_routes: assertion `iface != NULL' failed
Oct  8 18:15:07 domdesktop avahi-daemon[1083]: Withdrawing workstation service for tap0.
Oct  8 18:15:07 domdesktop NetworkManager[1085]: sync_addresses: assertion `iface != NULL' failed
Oct  8 18:15:07 domdesktop nm-openvpn[4036]: SIGTERM[hard,] received, process exiting
Oct  8 18:15:08 domdesktop NetworkManager[1085]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Oct  8 18:15:08 domdesktop NetworkManager[1085]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tap0, iface: tap0)
Oct  8 18:15:14 domdesktop NetworkManager[1085]: <info> VPN service 'openvpn' disappeared

```output of netstat -r
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         10.8.0.1        0.0.0.0         UG        0 0          0 tap0
10.8.0.0        10.8.0.2        255.255.255.0   UG        0 0          0 tun0
10.8.0.0        *               255.255.255.0   U         0 0          0 tap0
10.8.0.2        *               255.255.255.255 UH        0 0          0 tun0
localhost.local fritz.box       255.255.255.255 UGH       0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
192.168.178.0   *               255.255.255.0   U         0 0          0 eth0

```

---

