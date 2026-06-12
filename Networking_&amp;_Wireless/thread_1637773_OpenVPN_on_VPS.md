---
title: "OpenVPN on VPS"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by chanhuff on 2010-12-04
I am trying to setup OpenVPN on a VPS server.

I followed this guide and tried to edit my /etc/network/interfaces but it would not start after editing it so I undid the changes I made to it I have setup all of the Certificates I will paste my /var/log/daemon.log and /etc/network/interfaces file.

Message I Get When Starting OpenVPN
```

root@chanhuff:~# /etc/init.d/openvpn start
 * Starting virtual private network daemon(s)...
 *   Autostarting VPN 'openvpn'
 * Already running (PID file exists)
   ...done.
 *   Autostarting VPN 'server'
   ...fail!

```

/etc/network/interfaces
```

# Auto generated lo interface
auto lo
iface lo inet loopback

# Auto generated venet0 interface
auto venet0
iface venet0 inet static
        address 127.0.0.1
        netmask 255.255.255.255
        broadcast 0.0.0.0
        up route add -net 192.0.2.1 netmask 255.255.255.255 dev venet0
        up route add default gw 192.0.2.1

iface venet0 inet6 static
        address ::1
        netmask 128

auto venet0:0
iface venet0:0 inet static
        address 109.169.63.207
        netmask 255.255.255.255
        broadcast 0.0.0.0

auto venet0:1
iface venet0:1 inet static
        address 10.169.63.207
        netmask 255.255.255.255
        broadcast 0.0.0.0

```

/var/log/daemon.log
```

Dec  5 06:15:04 chanhuff named[22409]: listening on IPv4 interface tun0, 10.8.0.1#53
Dec  5 06:16:11 chanhuff ovpn-server[9225]: OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 12 2010
Dec  5 06:16:11 chanhuff ovpn-server[9225]: NOTE: when bridging your LAN adapter with the TAP adapter, note that the new bridge adapter will often take on its own IP address that is different from what the LAN adapter was previously set to
Dec  5 06:16:11 chanhuff ovpn-server[9225]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Dec  5 06:16:11 chanhuff ovpn-server[9225]: Diffie-Hellman initialized with 1024 bit key
Dec  5 06:16:11 chanhuff ovpn-server[9225]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Dec  5 06:16:11 chanhuff ovpn-server[9225]: Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Dec  5 06:16:11 chanhuff ovpn-server[9225]: Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Dec  5 06:16:11 chanhuff ovpn-server[9225]: Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Dec  5 06:16:11 chanhuff ovpn-server[9225]: TLS-Auth MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ]
Dec  5 06:16:11 chanhuff ovpn-server[9225]: RESOLVE: Cannot resolve host address: <your: [NO_RECOVERY] A non-recoverable name server error occurred.
Dec  5 06:16:11 chanhuff ovpn-server[9225]: Exiting

```

---

### Post by chanhuff on 2010-12-05
bump

---

