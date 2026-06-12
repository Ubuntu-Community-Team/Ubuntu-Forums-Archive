---
title: "Yet Another OVPN issue - routes fail"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by thepinkster on 2010-07-18
Howdy-

New ubuntu desktop user here. I've been working with Ubuntu servers for over 3 yrs, using Windows as clients. I have OpenVPN running on an ubuntu 10.04 server, and it has worked well with Windows OpenVPN clients connecting.

I took those same settings and applied them to this new install of Ubuntu 10.04 Desktop, and now openvpn seems to be failing when we get to the routes (I wrestled with the network-manager "secrets" issue for hours, but that works now).

I performed the following:

sudo openvpn --config fogbank-ny1.ovpn

--all is well, we're connecting/yay then *screech* FAIL--

```
Sun Jul 18 07:17:14 2010 PUSH: Received control message: 'PUSH_REPLY,route 10.8.0.0 255.255.255.0,redirect-gateway def1,dhcp-option DNS 10.8.0.1,route 10.8.0.0 255.255.255.0,topology net30,ping 30,ping-restart 600,ifconfig 10.8.0.10 10.8.0.9'
Sun Jul 18 07:17:14 2010 OPTIONS IMPORT: timers and/or timeouts modified
Sun Jul 18 07:17:14 2010 OPTIONS IMPORT: --ifconfig/up options modified
Sun Jul 18 07:17:14 2010 OPTIONS IMPORT: route options modified
Sun Jul 18 07:17:14 2010 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Sun Jul 18 07:17:14 2010 ROUTE default_gateway=192.168.10.1
Sun Jul 18 07:17:14 2010 TUN/TAP device tun0 opened
Sun Jul 18 07:17:14 2010 TUN/TAP TX queue length set to 100
Sun Jul 18 07:17:14 2010 /sbin/ifconfig tun0 10.8.0.10 pointopoint 10.8.0.9 mtu 1500
Sun Jul 18 07:17:14 2010 /sbin/route add -net <mypublicip> netmask 255.255.255.255 gw 192.168.10.1
Sun Jul 18 07:17:14 2010 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 10.8.0.9
Sun Jul 18 07:17:14 2010 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.8.0.9
Sun Jul 18 07:17:14 2010 /sbin/route add -net 10.8.0.0 netmask 255.255.255.0 gw 10.8.0.9
Sun Jul 18 07:17:14 2010 /sbin/route add -net 10.8.0.0 netmask 255.255.255.0 gw 10.8.0.9
SIOCADDRT: File exists
Sun Jul 18 07:17:14 2010 ERROR: Linux route add command failed: external program exited with error status: 7
Sun Jul 18 07:17:14 2010 Initialization Sequence Completed
```

I am using the suggested openvpn routes. If I connect from Windows (actually the .ovpn file is taken directly from the working windows machine).. all is well, routes work fine all traffic is routed thru the VPN -- same way it's worked for over a yar.

I assume that this is what is causing networkmanager to fail as well. those logs indicate that it has connected to the vpn, but is probably stopping when it gets to routes.

Thanks for any help on this issue, if i've forgotten anything else (more logs, route printouts, etc) let me know. i've spent the past 14 hours trying to debug it. I need more coffee.

---

### Post by thepinkster on 2010-07-18
Weird. I switched from 'TCP' to 'UDP' ... Still get the same errs on startup, but the link persists. All traffic goes over the VPN now. Before, after about 50 seconds, traffic would stop flowing between client / server. Now, it's been running for about 10 mins (I'm accessing the forum via the routed vpn connection using network-manager).

Well.. Don't know what to make of it. I'll re-test a Windows client in a bit using the new UDP settings.

---

