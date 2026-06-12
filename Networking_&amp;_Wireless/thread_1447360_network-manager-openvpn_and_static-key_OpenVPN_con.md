---
title: "network-manager-openvpn and static-key OpenVPN connection in 9.10"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by SysterNeoX on 2010-04-05
Hi all!

i have some problems with configuring openvpn tunnel connection to my openvpn server. I'm using static-key tcp connection. Network manager always said to me that connection could not be established. Also, when i try to run openvpn from terminal, i got some strange permissions problem:

```
openvpn --config config.ovpn
Mon Apr  5 15:48:37 2010 OpenVPN 2.1_rc19 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Mon Apr  5 15:48:37 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Mon Apr  5 15:48:37 2010 /usr/sbin/openvpn-vulnkey -q moj.key
Mon Apr  5 15:48:37 2010 WARNING: file 'moj.key' is group or others accessible
Mon Apr  5 15:48:37 2010 Static Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Apr  5 15:48:37 2010 Static Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Apr  5 15:48:37 2010 Static Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Apr  5 15:48:37 2010 Static Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Apr  5 15:48:37 2010 LZO compression initialized
Mon Apr  5 15:48:37 2010 Note: Cannot ioctl TUNSETIFF tun: Operation not permitted (errno=1)
Mon Apr  5 15:48:37 2010 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Mon Apr  5 15:48:37 2010 Cannot allocate TUN/TAP dev dynamically
Mon Apr  5 15:48:37 2010 Exiting
```
However, when i run it as a superuser (with prefix sudo) it works fine.

The /var/lib/daemon.log doesn't print anything interesting:
```
Apr  5 15:56:48 Syster-Laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Apr  5 15:56:48 Syster-Laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 3127
Apr  5 15:56:48 Syster-Laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
Apr  5 15:56:48 Syster-Laptop NetworkManager: <info>  VPN plugin state changed: 3
Apr  5 15:56:48 Syster-Laptop NetworkManager: <info>  VPN connection 'Po&#322;&#261;czenie VPN 1' (Connect) reply received.
Apr  5 15:56:48 Syster-Laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun1, iface: tun1)
Apr  5 15:56:48 Syster-Laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun1, iface: tun1): no ifupdown configuration found.
Apr  5 15:56:48 Syster-Laptop NetworkManager: <info>  VPN plugin failed: 2
Apr  5 15:56:48 Syster-Laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun1, iface: tun1)
Apr  5 15:56:48 Syster-Laptop NetworkManager: <info>  VPN plugin failed: 1
Apr  5 15:56:48 Syster-Laptop NetworkManager: <info>  VPN plugin state changed: 6
Apr  5 15:56:48 Syster-Laptop NetworkManager: <info>  VPN plugin state change reason: 0
Apr  5 15:56:48 Syster-Laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Apr  5 15:56:48 Syster-Laptop NetworkManager: <info>  Policy set 'Auto DOM' (eth1) as default for routing and DNS.
Apr  5 15:57:01 Syster-Laptop NetworkManager: <debug> [1270475821.003187] ensure_killed(): waiting for vpn service pid 3127 t
```

The question is the openvpn plugin for network manager really works?

---

### Post by Tweak42 on 2010-04-20
Hi, I had the same problem few months back with 9.04 and 9.10.  After a few hours of frustration, I gave up network-manager-openvpn and ended up writing a command line script.  I did learn a lot more about the workings of openvpn than I wanted, but my script still works on 10.04 beta as of this writing.

A quick search (now that I've gotten better at searching for bugs) on launchpad nets: 
[https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/451533](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/451533)
[https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/193686](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/193686)

---

