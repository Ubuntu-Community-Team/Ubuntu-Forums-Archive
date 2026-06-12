---
title: "OpenVPN issues"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by anathema415 on 2010-11-29
Hi guys,

Using Ubuntu 10.10

I have a VPN account with VPNtunnel.se. I configured everything as described on their site. It uses OpenVPN It connects no problem. However; after it connects instead of having a nice secure connection I have no connection at all! I can't access any site, email, bittorrent all come to a screeching hault. The service works fine in Windows. I'm useless with linux networking. Any suggestions?

---

### Post by anathema415 on 2010-11-30
Is there no one out there who can help me?

---

### Post by dawt on 2010-12-02
I'm having the same issues. I've contacted their support a few hours ago but they haven't replied yet.
I'll just post what I sent them, you might want to confirm you're having the same error as me. If VPN Tunnel Support responds with a solution, I'll post it.


> First off, I'm running Ubuntu 10.10 64bit.
Connecting works just fine manually and with the OpenVPN plugin for network-manager. But here's where the difficulties begin.
If I connect via the NM, i apparently can't find a route to the hosts  I'm trying to reach. I manually added your DNS servers (and looking up  IPs works now), but every attempt to connect to a server just pings out.
If I connect manually, the connection just breaks down after some time for no  apparent reason.

I've set up everything as described in the .pdf's for Linux and the NM.  Tests @ speedtest.net and pingtest.net also show my connection to be  excellent, so no idea why it stops working after a while.
Here's the output I get, when I connect manually... 
```

carl@carl-laptop:~$ sudo openvpn /etc/openvpn/openvpn.conf 
Thu Dec  2 19:04:22 2010 OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2]  [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 12 2010
Enter Auth Username:***
Enter Auth Password:
Thu Dec  2 19:04:39 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Thu Dec  2 19:04:39 2010 LZO compression initialized
Thu Dec  2 19:04:39 2010 RESOLVE: NOTE: ***.vpntunnel.se resolves to 9 addresses, choosing one by random
Thu Dec  2 19:04:39 2010 UDPv4 link local: [undef]
Thu Dec  2 19:04:39 2010 UDPv4 link remote: [AF_INET]178.***.***.***:10010
Thu Dec  2 19:04:39 2010 WARNING: this configuration may cache passwords  in memory -- use the auth-nocache option to prevent this
Thu Dec  2 19:04:40 2010 [server] Peer Connection Initiated with [AF_INET]178.***.***.***:10010
Thu Dec  2 19:04:42 2010 TUN/TAP device tap0 opened
Thu Dec  2 19:04:42 2010 /sbin/ifconfig tap0 178.***.***.*** netmask 255.255.255.0 mtu 1500 broadcast 178.***.***.255
Thu Dec  2 19:04:42 2010 Initialization Sequence Completed
Thu Dec  2 19:11:24 2010 [server] Inactivity timeout (--ping-restart), restarting
Thu Dec  2 19:11:24 2010 SIGUSR1[soft,ping-restart] received, process restarting
Thu Dec  2 19:11:26 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Thu Dec  2 19:11:26 2010 Re-using SSL/TLS context
Thu Dec  2 19:11:26 2010 LZO compression initialized
Thu Dec  2 19:11:26 2010 RESOLVE: NOTE: ***.vpntunnel.se resolves to 9 addresses, choosing one by random
Thu Dec  2 19:11:26 2010 UDPv4 link local: [undef]
Thu Dec  2 19:11:26 2010 UDPv4 link remote: [AF_INET]178.***.***.***:10010
Thu Dec  2 19:11:51 2010 read UDPv4 [EHOSTUNREACH]: No route to host (code=113)
Thu Dec  2 19:12:06 2010 read UDPv4 [EHOSTUNREACH]: No route to host (code=113)
Thu Dec  2 19:12:09 2010 read UDPv4 [EHOSTUNREACH]: No route to host (code=113)
Thu Dec  2 19:12:21 2010 read UDPv4 [EHOSTUNREACH]: No route to host (code=113)
Thu Dec  2 19:12:26 2010 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Thu Dec  2 19:12:26 2010 TLS Error: TLS handshake failed
Thu Dec  2 19:12:26 2010 SIGUSR1[soft,tls-error] received, process restarting
Thu Dec  2 19:12:28 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Thu Dec  2 19:12:28 2010 Re-using SSL/TLS context
Thu Dec  2 19:12:28 2010 LZO compression initialized
Thu Dec  2 19:12:28 2010 RESOLVE: NOTE: ***.vpntunnel.se resolves to 9 addresses, choosing one by random
Thu Dec  2 19:12:28 2010 UDPv4 link local: [undef]
Thu Dec  2 19:12:28 2010 UDPv4 link remote: [AF_INET]178.***.***.***:1194
Thu Dec  2 19:12:54 2010 read UDPv4 [EHOSTUNREACH]: No route to host (code=113)
Thu Dec  2 19:12:57 2010 read UDPv4 [EHOSTUNREACH]: No route to host (code=113)
Thu Dec  2 19:13:03 2010 read UDPv4 [EHOSTUNREACH]: No route to host (code=113)
Thu Dec  2 19:13:28 2010 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Thu Dec  2 19:13:28 2010 TLS Error: TLS handshake failed
```...etc etc


This is the output of the route command if I connect manually (note: the  output stays the same, even if the connection has broken down!)

```
carl@carl-laptop:~$ route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
178.***.***.*** speedport.ip    255.255.255.255 UGH   0      0        0 eth0
178.***.***.0   *               255.255.255.0   U     0      0        0 tap0
192.168.123.0   *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         v4-link.vpntunn 128.0.0.0       UG    0      0        0 tap0
128.0.0.0       v4-link.vpntunn 128.0.0.0       UG    0      0        0 tap0
default         speedport.ip    0.0.0.0         UG    0      0        0 eth0
```This is the output of the route command, if I try connecting via the network-manager:

```
carl@carl-laptop:~$ route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
178.***.***.*** speedport.ip    255.255.255.255 UGH   0      0        0 eth0
178.***.***.0   *               255.255.255.0   U     0      0        0 tap0
192.168.123.0   *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         v4-link.vpntunn 0.0.0.0         UG    0      0        0 tap0
```Concerning the network-manager, this is what I found in /var/log/daemon.log:

```
Dec  2 18:48:22 carl-laptop nm-openvpn[2615]: OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 12 2010
Dec  2 18:48:22 carl-laptop nm-openvpn[2615]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Dec  2 18:48:22 carl-laptop nm-openvpn[2615]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Dec  2 18:48:22 carl-laptop nm-openvpn[2615]: RESOLVE: NOTE: ***.vpntunnel.se resolves to 9 addresses, choosing one by random
Dec  2 18:48:22 carl-laptop nm-openvpn[2615]: UDPv4 link local: [undef]
Dec  2 18:48:22 carl-laptop nm-openvpn[2615]: UDPv4 link remote: [AF_INET]178.73.215.186:10020
Dec  2 18:48:22 carl-laptop nm-openvpn[2615]: WARNING: 'link-mtu' is used inconsistently, local='link-mtu 1573', remote='link-mtu 1574'
Dec  2 18:48:22 carl-laptop nm-openvpn[2615]: WARNING: 'comp-lzo' is present in remote config but missing in local config, remote='comp-lzo'
Dec  2 18:48:22 carl-laptop nm-openvpn[2615]: [server] Peer Connection Initiated with [AF_INET]178.***.***.***:10020
Dec  2 18:48:24 carl-laptop modem-manager: (net/tap0): could not get port's parent device
Dec  2 18:48:24 carl-laptop NetworkManager[921]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tap0, iface: tap0)
Dec  2 18:48:24 carl-laptop NetworkManager[921]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tap0, iface: tap0): no ifupdown configuration found.
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <warn> /sys/devices/virtual/net/tap0: couldn't determine device driver; ignoring...
Dec  2 18:48:24 carl-laptop nm-openvpn[2615]: TUN/TAP device tap0 opened
Dec  2 18:48:24 carl-laptop nm-openvpn[2615]: /sbin/ifconfig tap0 178.***.***.*** netmask 255.255.255.0 mtu 1500 broadcast 178.***.***.255
Dec  2 18:48:24 carl-laptop nm-openvpn[2615]: /usr/lib/network-manager-openvpn/nm-openvpn-service-openvpn-helper tap0 1500 1573 178.***.***.*** 255.255.255.0 init
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <info> VPN connection 'openvpn' (IP Config Get) reply received.
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <info> VPN Gateway: 178.***.***.***
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <info> Internal Gateway: 178.***.***.1
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <info> Tunnel Device: tap0
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <info> Internal IP4 Address: 178.***.***.***
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <info> Internal IP4 Prefix: 24
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <info> Internal IP4 Point-to-Point Address: 0.0.0.0
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <info> Maximum Segment Size (MSS): 0
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <info> Internal IP4 DNS: 80.67.0.2
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <info> Internal IP4 DNS: 91.213.246.2
Dec  2 18:48:24 carl-laptop NetworkManager[921]: <info> DNS Domain: '(none)'
Dec  2 18:48:24 carl-laptop nm-openvpn[2615]: Initialization Sequence Completed
Dec  2 18:48:25 carl-laptop NetworkManager[921]: <info> (tap0): writing resolv.conf to /sbin/resolvconf
Dec  2 18:48:25 carl-laptop NetworkManager[921]: <info> VPN connection 'openvpn' (IP Config Get) complete.
Dec  2 18:48:25 carl-laptop NetworkManager[921]: <info> (tap0): writing resolv.conf to /sbin/resolvconf
Dec  2 18:48:25 carl-laptop NetworkManager[921]: <info> Policy set 'openvpn' (tap0) as default for IPv4 routing and DNS.
Dec  2 18:48:25 carl-laptop NetworkManager[921]: <info> VPN plugin state changed: 4
Dec  2 18:48:25 carl-laptop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Dec  2 18:50:26 carl-laptop nm-openvpn[2615]: /sbin/ifconfig tap0 0.0.0.0
Dec  2 18:50:26 carl-laptop NetworkManager[921]: <info> (tap0): writing resolv.conf to /sbin/resolvconf
Dec  2 18:50:26 carl-laptop nm-openvpn[2615]: SIGTERM[hard,] received, process exiting
```I'm also having these issues (VPN connecting but not routing traffic) with Anonine.com and VPNSecure.me. SwissVPN.net is the only one I can get to properly connect via network-manager, yet the connection still tends to break after a couple of hours. Still, the connection remains stable a lot longer than with VPNtunnel.se

---

### Post by dawt on 2010-12-03
Alright, I think I've found the problem. You can easily confirm this by trying to connect to the VPN from a different location. Maybe at work, or at a friend's house. I'm suspecting the problem might be caused by the router, but I'm not certain yet.
Anyhow, the problem is UDP. Using a TCP connection instead worked wonders for me. Now vpntunnel.se doesn't offer TCP connections. Places that do, however are:
- SwissVPN.net ... PPTP and OpenVPN, stores connection logs (no traffic logs), I get around 4-5 Mbit. (I'm on a 16 Mbit connection, btw), based in Switzerland.
- ILikeItSafe.com ... PPTP (for smartphone only?) and OpenVPN, stores no logs, I get around 11-12 Mbit, based in Sweden. Hasn't opened to the public yet, though.

The other VPN providers that I've checked out in this price range that don't store logs etc unfortunately all only offer UDP connections.

---

### Post by anathema415 on 2010-12-07
Hidemyass vpn also works. They store connection logs for seven days but no traffic logs. Servers all over the world

---

### Post by dawt on 2010-12-16
Yup, it's definitely UDP and updating the firmware on my router solved the issue.
Whatever, I'm using ILikeItSafe.com now. They use verb 0 in OpenVPN, so there aren't any logs at all.

---

### Post by MedianN on 2011-01-04
How can it be a router issue if it works in Windows?

I am having the same problem. However, having a hard time to find firmware updates for my DLINK DSL-2640U

---

### Post by GGabor74 on 2011-01-06
Hi!
 
I've got the same problem with the Freeopenvpn.com:  connect ok, but no traffic to anywhere
 
Here is my topic (sorry for that) 
 
[http://ubuntuforums.org/showthread.php?t=1658384&highlight=vpn+routing](http://ubuntuforums.org/showthread.php?t=1658384&highlight=vpn+routing)

---

### Post by ryukent on 2011-10-26
I'm having the same problem with Ubuntu 11.10. I can connect to various VPNTunnel.se servers, but cannot access many websites. Originally I could access nothing. I removed the firewall (UFW) which was default installed but I still can't access certain site like gmail or paypal.co.uk

---

### Post by impr0b on 2011-12-09
Has anyone found a definite solution to this problem? I'm having the exact same issue. VpnTunnel.se worked fine on Win 7. On Ubuntu, I can connect to any of their servers with no issue, but after that I can't get any internet traffic. 
I've been on many forums with this question, and still waiting to hear back from VpnTunnel.se support. Anyone that could be of any assisstance, I would greatly appreciate it. Thank you in advance.

---

### Post by jonobr on 2011-12-09
Is there a setting for toggling LZO compression?

Did you try toggling it?

---

### Post by impr0b on 2011-12-09
jonobr, i want to kiss you. Turning the LZO compression on did it. Thank you soooo much.

---

### Post by jonobr on 2011-12-09
Lets just leave it at a solid handshake and a thanks....
(unless you are really Taylor Swift.....)

Recommend you mark as solved in the title though

Have great weekend

---

### Post by humblegeek on 2012-02-23
Thanks jonobr, love you!!!!:P

---

