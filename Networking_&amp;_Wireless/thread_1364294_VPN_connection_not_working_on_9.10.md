---
title: "VPN connection not working on 9.10"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by GAZ082 on 2009-12-25
Hi guys. I had a working OpenVPN connection (using UltraVPN services) for a couple of weeks on 9.10 and from one day to the other, stop working since then. Here i'm posting the log information i could retrieve from daemon.log for some good man to give me a hand with it. Thanks a lot!

PD: i get a resolv.conf error coz i locked the file to prevent the networkmanager to write it with garbage IPs. Unlocking it does not solve the problem.

```
Dec 25 18:46:02 Iridio NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Dec 25 18:46:02 Iridio NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 5758
Dec 25 18:46:02 Iridio NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
Dec 25 18:46:02 Iridio NetworkManager: <info>  VPN plugin state changed: 1
Dec 25 18:46:03 Iridio NetworkManager: <info>  VPN plugin state changed: 3
Dec 25 18:46:03 Iridio NetworkManager: <info>  VPN connection 'UltraVPN' (Connect) reply received.
Dec 25 18:46:03 Iridio nm-openvpn[5764]: OpenVPN 2.1_rc19 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Dec 25 18:46:03 Iridio nm-openvpn[5764]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Dec 25 18:46:03 Iridio nm-openvpn[5764]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Dec 25 18:46:03 Iridio nm-openvpn[5764]: UDPv4 link local: [undef]
Dec 25 18:46:03 Iridio nm-openvpn[5764]: UDPv4 link remote: 87.98.173.225:443
Dec 25 18:46:03 Iridio nm-openvpn[5764]: read UDPv4 [ECONNREFUSED]: Connection refused (code=111)
Dec 25 18:46:43 Iridio nm-openvpn[5764]: last message repeated 18 times
Dec 25 18:46:43 Iridio NetworkManager: <info>  VPN connection 'UltraVPN' (IP Config Get) timeout exceeded.
Dec 25 18:46:43 Iridio nm-openvpn[5764]: SIGTERM[hard,] received, process exiting
Dec 25 18:46:43 Iridio NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf
Dec 25 18:46:43 Iridio NetworkManager: <WARN>  nm_named_manager_add_ip4_config(): Could not commit DNS changes.  Error: 'Could not replace /etc/resolv.conf: Operation not permitted#012'
Dec 25 18:46:43 Iridio NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Dec 25 18:46:55 Iridio NetworkManager: <debug> [1261777615.002498] ensure_killed(): waiting for vpn service pid 5758 to exit
Dec 25 18:46:55 Iridio NetworkManager: <debug> [1261777615.002884] ensure_killed(): vpn service pid 5758 cleaned up
```

---

