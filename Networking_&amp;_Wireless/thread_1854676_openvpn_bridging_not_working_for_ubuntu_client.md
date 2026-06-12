---
title: "openvpn bridging not working for ubuntu client"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by foxbeard on 2011-10-04
I have a bridged openvpn setup on my home router. I can connect to it and have everything working fine from windows clients, but no such luck on my ubuntu laptop.

The server is a DD-WRT router, and it seems to be working fine. Windows is able to connect as expected, as mentioned above.

server startup script:
```
openvpn --mktun --dev tap0 
brctl addif br0 tap0
ifconfig tap0 0.0.0.0 promisc up
echo "-----BEGIN OpenVPN Static key V1-----
-----END OpenVPN Static key V1-----" > /tmp/static.key
ln -s /usr/sbin/openvpn /tmp/myvpn
echo 1 > /proc/sys/net/ipv4/ip_forward
echo "dev tap0
secret /tmp/static.key
port 1194
proto
udp
keepalive 10 60
ping-timer-rem
persist-tun
persist-key
comp-lzo" > /tmp/server.conf
/tmp/myvpn --config /tmp/server.conf --daemon
```I have to use static key due to space restrictions. Trying to store all of the keys and certificates for TLS bricks my router.

The client is Ubuntu 11.04, using openvpn from the repos
client config:
```

remote <my ip>
dev tap
proto udp
port 1194
secret static.key
keepalive 10 60
ping-timer-rem
persist-tun
persist-key
comp-lzo
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf
script-security 2

```I'm running openvpn from the console, as TAP is completely broken in the network-manager plugin.

When I start the client,  It appears to connect to the server correctly. (Peer connection Initiated ... Initialization Sequence complete), but am unable to ping anything on the home network.
The problem appears to be that:
1) though openvpn creates the tap0 device, it does not initialize it. ifconfig reports it as down
2) /etc/resolv.conf is not being updated properly, despite running the resolvconf script
3) no routing is being set up.

I have very little experience in networking; I'm trying to get this set up as a learning exercise. I imagine that there are ways to do all of the interface and routing setup manually, but I haven't been able to figure it out yet. Still, it seems like openvpn ought to be doing it automatically.

I've found several other posts around the web with the same problem (bridged openvpn, windows client works fine, linux client fails) , but none have had an answer that has worked.

Has anyone been able to get a setup like this working?

---

