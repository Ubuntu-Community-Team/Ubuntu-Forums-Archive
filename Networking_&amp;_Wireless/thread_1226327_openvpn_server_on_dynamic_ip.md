---
title: "openvpn server on dynamic ip"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by omax on 2009-07-29
Hi!

I'm trying to set up an openvpn server on my box, that connects directly to the internet with a dynamic ip. As far as I know, i have to set my local IP in the configuration but since it's dynamic I don't know what to do.

the box is always updated with a dyndns domain using ddclient.
server.conf
```
dev tun

local mydomain
port 1194
proto udp

tls-server
ca /etc/openvpn/examples/easy-rsa/keys/ca.crt 
cert /etc/openvpn/examples/easy-rsa/keys/server.crt 
key /etc/openvpn/examples/easy-rsa/keys/server.key
dh /etc/openvpn/examples/easy-rsa/keys/dh2048.pem

#ifconfig-pool-persist ipp.txt

keepalive 10 120

cipher AES-128-CBC

tls-auth ta.key 0

comp-lzo
user nobody
group nogroup
persist-key
persist-tun

```

```
# openvpn server.conf
Wed Jul 29 20:19:32 2009 OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on May  8 2009
Wed Jul 29 20:19:32 2009 /usr/bin/openssl-vulnkey -q -b 2048 -m <modulus omitted>
Wed Jul 29 20:19:32 2009 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Wed Jul 29 20:19:32 2009 LZO compression initialized
Wed Jul 29 20:19:32 2009 TUN/TAP device tap0 opened
Wed Jul 29 20:19:32 2009 GID set to nogroup
Wed Jul 29 20:19:32 2009 UID set to nobody
Wed Jul 29 20:19:32 2009 UDPv4 link local (bound): my.external.ip:1194
Wed Jul 29 20:19:32 2009 UDPv4 link remote: [undef]


```

When I try to connect to port 1194 using netcat I get connection refused, so it's not up and running.

---

