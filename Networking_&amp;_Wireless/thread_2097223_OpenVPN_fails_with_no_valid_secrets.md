---
title: "OpenVPN fails with no valid secrets"
date: 2012-12-22
forum: Networking &amp; Wireless
---

### Post by yedd on 2012-12-22
Hello all, I am using ipredator vpn and followed the instructions here: [https://www.ipredator.se/guide/openvpn/ubuntu/gnome](https://www.ipredator.se/guide/openvpn/ubuntu/gnome)

My setup is exactly as they have instructed, but when I connect, the network manager tells me that it failed due to having no valid secrets.

My credentials should be correct because I previously used the old method of connecting (with pptp) and it would log me in.

I've already restarted the network-manager service and even rebooted my machine.

My syslog shows:

```
Dec 22 11:36:13 desktop-1 NetworkManager[972]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 3215
Dec 22 11:36:13 desktop-1 NetworkManager[972]: <info> VPN service 'openvpn' appeared; activating connections
Dec 22 11:36:13 desktop-1 NetworkManager[972]: <info> VPN plugin state changed: 1
Dec 22 11:36:13 desktop-1 NetworkManager[972]: <info> VPN plugin state changed: 3
Dec 22 11:36:13 desktop-1 NetworkManager[972]: <info> VPN connection 'Ipredator-openvpn' (Connect) reply received.
Dec 22 11:36:13 desktop-1 nm-openvpn[3219]: OpenVPN 2.2.0 i686-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Jul  4 2011
Dec 22 11:36:14 desktop-1 NetworkManager[972]: <info> (wlan0): IP6 addrconf timed out or failed.
Dec 22 11:36:14 desktop-1 NetworkManager[972]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Dec 22 11:36:14 desktop-1 NetworkManager[972]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) started...
Dec 22 11:36:14 desktop-1 NetworkManager[972]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Dec 22 11:36:14 desktop-1 NetworkManager[972]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 22 11:36:14 desktop-1 NetworkManager[972]: <info> Activation (wlan0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Dec 22 11:36:14 desktop-1 nm-openvpn[3219]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Dec 22 11:36:14 desktop-1 nm-openvpn[3219]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Dec 22 11:36:14 desktop-1 nm-openvpn[3219]: WARNING: file '/home/desktop/vpn/IPredator.se.ta.key' is group or others accessible
Dec 22 11:36:14 desktop-1 nm-openvpn[3219]: Control Channel Authentication: using '/home/desktop/vpn/IPredator.se.ta.key' as a OpenVPN static key file
Dec 22 11:36:14 desktop-1 nm-openvpn[3219]: LZO compression initialized
Dec 22 11:36:14 desktop-1 nm-openvpn[3219]: RESOLVE: NOTE: pw.openvpn.ipredator.se resolves to 10 addresses
Dec 22 11:36:14 desktop-1 nm-openvpn[3219]: UDPv4 link local: [undef]
Dec 22 11:36:14 desktop-1 nm-openvpn[3219]: UDPv4 link remote: [AF_INET]xxx.xxx.xxx
Dec 22 11:36:16 desktop-1 nm-openvpn[3219]: [pw.openvpn.ipredator.se] Peer Connection Initiated with [AF_INET]xxx.xxx.xxx
Dec 22 11:36:19 desktop-1 nm-openvpn[3219]: AUTH: Received AUTH_FAILED control message
Dec 22 11:36:19 desktop-1 nm-openvpn[3219]: SIGTERM[soft,auth-failure] received, process exiting
Dec 22 11:36:19 desktop-1 NetworkManager[972]: <warn> VPN plugin failed: 0
Dec 22 11:36:19 desktop-1 NetworkManager[972]: <info> VPN plugin state changed: 6
Dec 22 11:36:19 desktop-1 NetworkManager[972]: <info> VPN plugin state change reason: 10
Dec 22 11:36:19 desktop-1 NetworkManager[972]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Dec 22 11:36:19 desktop-1 NetworkManager[972]: <info> Policy set 'wireless' (wlan0) as default for IPv4 routing and DNS.
Dec 22 11:36:25 desktop-1 NetworkManager[972]: <info> VPN service 'openvpn' disappeared
```


Could someone provide some suggestions?

---

### Post by ahallubuntu on 2012-12-22
Check to make sure the CA Certificate is really being found.  You can go back into the OpenVPN configuration and make sure "IPredator.se.ca.crt" is really pointing to the right place.

I've had issues using the Import feature of the Network Manager OpenVPN plug in before.  Manually setting up the connection may work instead.  I use OpenVPN all the time and it works great for me - but I have my own OpenVPN server not someone else's.  Of course, ask them.

---

