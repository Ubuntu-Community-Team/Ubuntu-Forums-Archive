---
title: "Double VPN connection: openvpn over vpnc"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by Frando on 2011-05-26
hello,

i have the following situation:

In my wireless network, i have to connect to a cisco vpn (with vpnc) to access the internet. Now I want to route all traffic through a second vpn (with openvpn) for anonymity purposes.

So this is what it should look like:

my computer, wlan0 --> vpnc vpn --> openvpn vpnc --> internet

now, when I connect to the vpnc vpn (with kvpnc, or with vpnc-connect) i can access the internet and get an IP, say "IP a.b.c.d" on a device tun0.

if I now create the openvpn network (with openvpn config.ovpn), it creates another device, tun1, with another IP, say "IP e.f.g.h".

[B]But if I then start firefox or anything else accessing the internet, it seems to use tun0, so my IP is reported as "IP a.b.c.d". I want to access the internet via the openvpnc connection, though (tun1 and IP e.f.g.h)

How can I achieve that?
[/B]

(i'm on Kubuntu 10.04)

Some data that might help you:
```

# cat config.ovpn
client
dev tun
remote vpn.xxx.net
auth-user-pass
ca certificate-xxx.pem
push "redirect-gateway def1"


# openvpn config.ovpn

Thu May 26 14:07:39 2011 UDPv4 link local (bound): [undef]
Thu May 26 14:07:39 2011 UDPv4 link remote: [AF_INET]x.x.x.x:1194
Thu May 26 14:07:39 2011 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Thu May 26 14:07:41 2011 [vpn.xxx.net] Peer Connection Initiated with [AF_INET]x.x.x.x:1194
Thu May 26 14:07:44 2011 TUN/TAP device tun1 opened
Thu May 26 14:07:44 2011 /sbin/ifconfig tun1 [e.f.g.h] netmask 255.255.252.0 mtu 1500 broadcast [e.f.g.255]
Thu May 26 14:07:44 2011 NOTE: unable to redirect default gateway -- Cannot read current default gateway from system
Thu May 26 14:07:44 2011 Initialization Sequence Completed

# ifconfig

tun0      Link encap:UNSPEC  Hardware Adresse 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet Adresse:[a.b.c.d]  P-z-P:[a.b.c.d]  Maske:255.255.255.255

tun1      Link encap:UNSPEC  Hardware Adresse 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet Adresse:[e.f.g.h]  P-z-P:[e.f.g.h]  Maske:255.255.252.0

wlan0     Link encap:Ethernet  Hardware Adresse 00:13:e8:e9:ac:c7
          inet Adresse:x.y.4.79  Bcast:x.y.255.255  Maske:255.255.0.0


```

---

### Post by floorripper on 2011-09-28
Hello,

The issue might be with your routing table and Default Gateway handling.
All of your traffic is now being sent via the second vpn tunnel.

I would specify the routing manually, e.g. choose which traffic to send to which Tun0 interface and so one.

------------
EXAMPLE
------------

# Gateway script - use static routes for interesting traffic to specify routing
[I]route add  -net 10.149.0.0 netmask 255.255.0.0  tun0
route add  -net 11.25.211.108 netmask 255.255.255.255 tun0
route add  -net 0.0.0.0 netmask 0.0.0.0 gw 10.229.111.254 eth0  [/I]

# I have added default gateway to my firewall via normal eth0 to obey encryption of normal unimportant VPN traffic
*route add  -net 0.0.0.0 netmask 0.0.0.0 gw 10.229.111.254 eth0*

#delete the forced default gateway settings from vpn concentrator
*route del  -net 0.0.0.0 netmask 0.0.0.0 gw 0.0.0.0 tun0 *

---

### Post by floorripper on 2011-09-28
this is from** [COLOR=Blue]man vpnc[/COLOR]**

this might solve issue with routing to two tunnels as well.

[COLOR=Blue]Custom route setting
              By default, the default route is deleted after connection and replaced with the new one
              (going  trough  the  VPN  tunnel device). However, some people wish to limit the target
              address range to few IP ranges.  This can be done using  the  config  directive  Target
              networks in the config file. For example:
              Target networks 123.234.210.0/24 10.1.0.0/16[/COLOR]

---

