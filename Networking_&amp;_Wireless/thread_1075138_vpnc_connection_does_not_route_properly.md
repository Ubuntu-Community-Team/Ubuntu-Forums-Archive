---
title: "vpnc connection does not route properly"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by which_dan on 2009-02-20
I can get a vpnc connection either by command line or NetworkManager (yay).

```
NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 16879 
NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections 
NetworkManager: <info>  VPN plugin state changed: 1 
NetworkManager: <info>  VPN plugin state changed: 3 
NetworkManager: <info>  VPN connection 'Campus' (Connect) reply received. 
NetworkManager: <info>  VPN connection 'Campus' (IP Config Get) reply received. 
NetworkManager: <info>  VPN Gateway: 129.xxxxxxx.40 
NetworkManager: <info>  Tunnel Device: tun0 
NetworkManager: <info>  Internal IP4 Address: 129.xxxxx.10 
NetworkManager: <info>  Internal IP4 Prefix: 24 
NetworkManager: <info>  Internal IP4 Point-to-Point Address: 129.xxxxxx.10 
NetworkManager: <info>  Maximum Segment Size (MSS): 0 
NetworkManager: <info>  Static Route: 12x.xxxxxx.0/16   Next Hop: 12x.xxxxx.0 
NetworkManager: <info>  Static Route: 19x.xxxxxx.0/24   Next Hop: 19x.xxxxxx.0 
NetworkManager: <info>  Static Route: 19x.xxxxxx.0/24   Next Hop: 19x.xxxxxx.0 
NetworkManager: <info>  Static Route: 19x.xxxxxx.0/24   Next Hop: 19x.xxxxxx.0 
NetworkManager: <info>  Static Route: 10.0.0.0/8   Next Hop: 10.0.0.0 
NetworkManager: <info>  Internal IP4 DNS: 12x.xxxxxxx.x 
NetworkManager: <info>  Internal IP4 DNS: 12x.xxxxxxx.x 
NetworkManager: <info>  DNS Domain: 'xxxxxxxxx' 
NetworkManager: <info>  Login Banner: 
NetworkManager: <info>  ----------------------------------------- 
NetworkManager: <info>  Staff Virtual Private Network^M
NetworkManager: <info>  ----------------------------------------- 
NetworkManager: <info>  VPN connection 'Campus' (IP Config Get) complete. 
NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
NetworkManager: <info>  VPN plugin state changed: 4 
```

I can name resolution but pinging to any machine outside my home network gives me this:

```
$ ping xxxxxxxxxxxxxxxxxxx
PING adelaide.edu.au (19x.xxxxxx.xxx) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- xxxxxxxxxxxx ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3000ms
```

I suspect that the problem is routing, but I've tried to sort it out manually with no success. This is what the routing table looks like:

```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
vpn.xxxxxxx.ad gateway.home    255.255.255.255 UGH   0      0        0 eth0
12x.xxxxxx.0   *               255.255.255.0   U     0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
19x.xxxxxxx.0    *               255.255.255.0   U     0      0        0 tun0
19x.xxxxxxx.0    *               255.255.255.0   U     0      0        0 tun0
19x.xxxxxxx.0    *               255.255.255.0   U     0      0        0 tun0
12x.xxxxxx.0     *               255.255.0.0     U     0      0        0 tun0
10.0.0.0        *               255.0.0.0       U     0      0        0 tun0
default         gateway.home    0.0.0.0         UG    0      0        0 eth0

```

Any ideas?

---

### Post by j0rd on 2009-02-26
problem fix for me was disabling ipmasq by running "/etc/init.d/ipmasq stop" as root.

Here's the thread where i found the answer:
[http://ubuntuforums.org/showthread.php?t=1041028&highlight=sendmsg%3A+operation+not+permitted](http://ubuntuforums.org/showthread.php?t=1041028&highlight=sendmsg%3A+operation+not+permitted)


I was having the same issue with ping operation not permitted, where everything else looked correct.

---

### Post by which_dan on 2009-02-26
Yeah that is consistent with what I found to fix the problem. I turned of the firewall with firestarter and it worked. Unfortunately I think the vpnc and my VPN dynamically assign ports for the tunnel, so I can't reliably punch a hole through while leaving the firewall up.

I'm reasonably happy with the solution, but advise about firewall management with vpnc would be cool.

---

