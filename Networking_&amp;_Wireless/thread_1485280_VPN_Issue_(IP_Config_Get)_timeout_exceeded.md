---
title: "VPN Issue (IP Config Get) timeout exceeded"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by bu3askoor on 2010-05-16
Hello All,
I've been trying to solve this issue for more than a week without any success.  I am using Witopia VPN services and used to work just fine on my Ubuntu 10.04.  All of the sudden it stopped working.  Here is the log:

```

May 17 00:56:58 saeed-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
May 17 00:56:58 saeed-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 11477
May 17 00:56:58 saeed-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
May 17 00:56:58 saeed-laptop NetworkManager: <info>  VPN plugin state changed: 1
May 17 00:56:58 saeed-laptop NetworkManager: <info>  VPN plugin state changed: 3
May 17 00:56:58 saeed-laptop NetworkManager: <info>  VPN connection 'VPN Connection' (Connect) reply received.
May 17 00:56:58 saeed-laptop nm-openvpn[11482]: OpenVPN 2.1.0 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jan 26 2010
May 17 00:56:58 saeed-laptop nm-openvpn[11482]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
May 17 00:56:58 saeed-laptop nm-openvpn[11482]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
May 17 00:56:58 saeed-laptop nm-openvpn[11482]: WARNING: file '/home/saeed/Documents/config/VPN_Connection.key' is group or others accessible
May 17 00:56:58 saeed-laptop nm-openvpn[11482]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
May 17 00:56:58 saeed-laptop nm-openvpn[11482]: LZO compression initialized
May 17 00:56:59 saeed-laptop nm-openvpn[11482]: RESOLVE: NOTE: (address omitted) resolves to 12 addresses, choosing one by random
May 17 00:56:59 saeed-laptop nm-openvpn[11482]: UDPv4 link local: [undef]
May 17 00:56:59 saeed-laptop nm-openvpn[11482]: UDPv4 link remote: [AF_INET]IP address omitted
May 17 00:57:39 saeed-laptop NetworkManager: <info>  VPN connection 'VPN Connection' (IP Config Get) timeout exceeded.
May 17 00:57:39 saeed-laptop nm-openvpn[11482]: SIGTERM[hard,] received, process exiting
May 17 00:57:39 saeed-laptop NetworkManager: <info>  Policy set 'Auto Belkin' (wlan0) as default for routing and DNS.
May 17 00:57:51 saeed-laptop NetworkManager: <debug> [1274043471.002409] ensure_killed(): waiting for vpn service pid 11477 to exit
May 17 00:57:51 saeed-laptop NetworkManager: <debug> [1274043471.002596] ensure_killed(): vpn service pid 11477 cleaned up

```

Please note i removed IP addresses.  I think i a recent update might have created this issue.  I tried re-installing openvpn and network-manager-openvpn.

Thanks

---

### Post by bu3askoor on 2010-05-16
I re-issued the key and cert from provider.  Now everything is working fine.  --embarrassing :)

---

