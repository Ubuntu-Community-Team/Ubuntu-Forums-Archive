---
title: "openvpn and default gw conflict"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by muscken on 2009-05-20
hi guys,
i've some difficult to configure openvpn on ubuntu...the vpn works fine,get an ip from dhcpd (172.16.0.0) an then,after 15 seconds,adds routes.the problem is that sometimes can't delete default gateway route.this is my client [conf.it]("http://conf.it/") get default gateway options both from server with pull and client with last two lines (i've tried to comment them but the problem persists).
remote 192.84.x.x 5003
dev tap
proto tcp
client
auth-user-pass
script-security 3 system
up /etc/openvpn/openvpn-up.sh (this script gets only ip with dhclient)
up-delay
route-delay 15
ca /etc/openvpn/keysprova/CA1.crt
verb 7
pull
route-gateway 172.16.8.1
redirect-gateway

this is route -n before vpn starts
10.y.0.0      0.0.0.0         255.255.0.0     U     1      0        0 eth0
0.0.0.0         10.y.0.1      0.0.0.0         UG    0      0        0 eth0
and this after routes has ben added
192.84.x.x    10.y.0.1      255.255.255.255 UGH   0      0        0 eth0
172.16.0.0      0.0.0.0         255.255.0.0     U     0      0        0 tap0
10.y.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         172.16.8.1      0.0.0.0         UG    0      0        0 tap0
0.0.0.0         10.y.0.1      0.0.0.0         UG    0      0        0 eth0
as you can see openvpn couldn't delete 10.y.0.1 default gateway
in the log i can see this
Wed May 20 10:30:54 2009 us=46519 /sbin/route add -net 192.84.x.x netmask 255.255.255.255 gw 10.y.0.1
Wed May 20 10:30:54 2009 us=48446 /sbin/route del -net 0.0.0.0 netmask 0.0.0.0
Wed May 20 10:30:54 2009 us=50230 /sbin/route add -net 0.0.0.0 netmask 0.0.0.0 gw 172.16.8.1
seems that the second line doesn't remove 10.y.0.1 default route.if i try to give command from console the route persist!
how can i solve?1 week ago i solved with 
route-up "/sbin/route del -net default gw 0.0.0.0 dev eth0"
but is horrible,if it's possible i prefere an automatic solution.with fedora there aren't these route problems...

---

