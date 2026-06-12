---
title: "Openvpn client fails"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by blwegrzyn on 2010-01-09
Hello,
I have openvpn server configured with bridged interface on my openwrt router. The client is running ubuntu 9.10 with config:
client
dev tap
proto udp
remote x.x.x.x 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca /home/blwegrzyn/openvpn/ca.crt
cert /home/blwegrzyn/openvpn/client1.crt
key /home/blwegrzyn/openvpn/client1.key
comp-lzo
verb 5

(x.x.x.x was hidden)

when the client connects the log says:

WRRRWRSat Jan  9 20:16:03 2010 us=332404 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway,dhcp-option DNS 192.168.1.241,route-gateway 192.168.1.254,ping 10,ping-restart 120'
Sat Jan  9 20:16:03 2010 us=332563 OPTIONS IMPORT: timers and/or timeouts modified
Sat Jan  9 20:16:03 2010 us=332597 OPTIONS IMPORT: route options modified
Sat Jan  9 20:16:03 2010 us=332622 OPTIONS IMPORT: route-related options modified
Sat Jan  9 20:16:03 2010 us=332646 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Sat Jan  9 20:16:03 2010 us=332916 ROUTE default_gateway=192.168.2.254
Sat Jan  9 20:16:03 2010 us=335251 TUN/TAP device tap0 opened
Sat Jan  9 20:16:03 2010 us=335310 TUN/TAP TX queue length set to 100
Sat Jan  9 20:16:03 2010 us=335416 /sbin/route add -net 99.177.129.250 netmask 255.255.255.255 gw 192.168.2.254
Sat Jan  9 20:16:03 2010 us=337907 /sbin/route del -net 0.0.0.0 netmask 0.0.0.0
Sat Jan  9 20:16:03 2010 us=342826 /sbin/route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.1.254
SIOCADDRT: No such process
Sat Jan  9 20:16:03 2010 us=343906 ERROR: Linux route add command failed: external program exited with error status: 7

the server is trying to push default gateway 192.168.1.254 to the client and the client is on 192.168.2.0 network
as you can see the route addition fails with SIOCADDRT: No such process

this is because the tap interface does not have any ip and the route addition is not possible

the tap interface is not getting the dhcp address through the tunnel, not sure why (this works on XP)

to fix the problem i must manually add the ip to the tap interface, and the default gateway, but then i must add dhcp server to resolv.conf to make it work
and once I disconnect the computer does not know the old valid dhcp anymore and cannot communicate

why openvpn cannot get the ip automatically ?
why it cannot grab the dhcp from the tunnel?

is it related to the wireless card being managed by the network manager?

this works perfect on windows machine (xp sp3)


thx

---

### Post by vlatkop on 2010-01-30
I am having the same problem and I must say that it is very, very annoying. More about configurations:

- OpenVPN Server installed on Debian Lenny 5.0.4
```
# cat /etc/openvpn/server.conf
port 1195
proto tcp
dev tap0
ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key
dh /etc/openvpn/easy-rsa/keys/dh2048.pem
ifconfig-pool-persist ipp.txt
server-bridge 10.1.1.0 255.255.255.0 10.1.1.236 10.1.1.245
push "route 10.1.1.0 255.255.255.0"
push "dhcp-option DNS 10.1.1.2"
keepalive 10 120
comp-lzo
persist-key
persist-tun
status /var/log/openvpn-status.log
verb 3

# uname -r
2.6.26-2-686

```

- Client machine:
```

# cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

# uname -r
2.6.31-18-generic

# apt-cache show openvpn
Package: openvpn
Priority: optional
Section: net
Installed-Size: 1176
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Alberto Gonzalez Iniesta <agi@inittab.org>
Architecture: i386
Version: 2.1~rc19-1ubuntu2
Depends: debconf (>= 0.5) | debconf-2.0, libc6 (>= 2.4), liblzo2-2, libpam0g (>= 0.99.7.1), libpkcs11-helper1 (>= 1.05), libssl0.9.8 (>= 0.9.8g-9), openssl-blacklist (>= 0.4), openvpn-blacklist, lsb-base (>= 3.2-14)
Recommends: net-tools
Suggests: openssl, resolvconf
Filename: pool/main/o/openvpn/openvpn_2.1~rc19-1ubuntu2_i386.deb
Size: 411552
MD5sum: d07a070f542ee73bc3157eb29f1f5659
SHA1: cfd5c3c3be692698826183b793a6547ea93e14c5
SHA256: 1a874ee52da73f8c636e4307d1695e90261a8a35c755f3de1f8f52275cd168ef
Description: virtual private network daemon
 OpenVPN is an application to securely tunnel IP networks over a
 single UDP or TCP port. It can be used to access remote sites, make
 secure point-to-point connections, enhance wireless security, etc.
 .
 OpenVPN uses all of the encryption, authentication, and certification
 features provided by the OpenSSL library (any cipher, key size, or
 HMAC digest).
 .
 OpenVPN may use static, pre-shared keys or TLS-based dynamic key exchange. It
 also supports VPNs with dynamic endpoints (DHCP or dial-up clients), tunnels
 over NAT or connection-oriented stateful firewalls (such as Linux's iptables).
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

# cat client.ovpn
client
dev tap
proto tcp
remote 1.2.3.4 1195 # (replace with your server IP)
resolv-retry infinite
nobind
pkcs12 client.p12 # (replace with the client name)
ns-cert-type server
comp-lzo
verb 3

```

---

### Post by vlatkop on 2010-02-23
I found the mistake that I have made:

```

# ip addr show br0
4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN 
    link/ether 00:16:3e:4f:bd:20 brd ff:ff:ff:ff:ff:ff
    inet 10.1.1.164/24 brd 10.1.1.255 scope global br0
    inet6 fe80::216:3eff:fe4f:bd20/64 scope link 
       valid_lft forever preferred_lft forever

```

so, the line:

```

server-bridge 10.1.1.0 255.255.255.0 10.1.1.236 10.1.1.245

```

should be:

```

server-bridge 10.1.1.164 255.255.255.0 10.1.1.236 10.1.1.245

```

But now push dns options are not working well... I guess it is firewall problem.

Regards, Vlado

---

### Post by vlatkop on 2010-02-23
[http://www.phocean.net/2006/12/07/openvpn-and-dns-on-a-linux-client.html](http://www.phocean.net/2006/12/07/openvpn-and-dns-on-a-linux-client.html)

grrrrrr

---

