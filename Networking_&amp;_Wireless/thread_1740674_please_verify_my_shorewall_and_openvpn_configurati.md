---
title: "please verify my shorewall and openvpn configurations"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by mkhurram92 on 2011-04-27
hello all there ???
i am configuring my OpenVPN on ubuntu 10.10 while i have shorewall also installed on it acting as a gateway to the network.
Please verify my configuraions
Shorewall Configuration is under 

Zones:-
#ZONE   TYPE    OPTIONS                 IN                      OUT
#                                       OPTIONS                 OPTIONS
fw      firewall
loc     ipv4
net     ipv4
vpn	ipv4				#

Interfaces:-
loc     eth1    detect
net     ppp0    -       optional
loc     eth0    detect
loc     tun+    detect  optional
vpn     ppp+    detect  optional

Policy:-
#loc     net     ACCEPT
$FW     all     ACCEPT
loc     $FW     ACCEPT
vpn     $FW     ACCEPT
vpn     loc     ACCEPT
loc     vpn     ACCEPT
all     all     REJECT

Rules:-
ACCEPT	net	$FW     udp	1194

Please let know why this error is occuring while i am going to connect my OpenVPN on client Side... !!

Wed Apr 27 15:52:31 2011 OpenVPN 2.1.4 i686-pc-mingw32 [SSL] [LZO2] [PKCS11] built on Nov  8 2010
Wed Apr 27 15:52:31 2011 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Wed Apr 27 15:52:31 2011 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Wed Apr 27 15:52:31 2011 LZO compression initialized
Wed Apr 27 15:52:31 2011 Control Channel MTU parms [ L:1539 D:138 EF:38 EB:0 ET:0 EL:0 ]
Wed Apr 27 15:52:31 2011 RESOLVE: NOTE: nasrinefactory.dyndnd.org resolves to 2 addresses
Wed Apr 27 15:52:31 2011 Data Channel MTU parms [ L:1539 D:1450 EF:39 EB:135 ET:0 EL:0 AF:3/1 ]
Wed Apr 27 15:52:31 2011 Local Options hash (VER=V4): 'b3f2f4a1'
Wed Apr 27 15:52:31 2011 Expected Remote Options hash (VER=V4): '2c67b116'
Wed Apr 27 15:52:31 2011 UDPv4 link local: [undef]
Wed Apr 27 15:52:31 2011 UDPv4 link remote: 64.20.60.99:1194
Wed Apr 27 15:53:32 2011 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Wed Apr 27 15:53:32 2011 TLS Error: TLS handshake failed
Wed Apr 27 15:53:32 2011 TCP/UDP: Closing socket
Wed Apr 27 15:53:32 2011 SIGUSR1[soft,tls-error] received, process restarting


i think problem is in my shorewall rules
please look into this :)

---

