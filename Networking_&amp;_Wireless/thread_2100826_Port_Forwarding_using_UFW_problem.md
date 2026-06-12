---
title: "Port Forwarding using UFW problem"
date: 2013-01-02
forum: Networking &amp; Wireless
---

### Post by Tylerjd on 2013-01-02
Let me first begin by explaining what I would like to get done. Basically, I have a publicly facing VPN server (a VPS at Linode), using OpenVPN to allow clients to connect. Now those clients are all servers behind a restrictive firewall but are able to connect to the VPN server successfully (can get pings from other VPN clients, etc). What I would like to do is have an incoming request, say, over port 2222 get NAT'd to the VPN interface (tap0, which is bridged to openvpnbr0) and delivered to a client on port 22. My rules, in theory should work, and I have net.ipv4.ip_forward in sysctl.conf set to 1. Below is are the relevant lines in /etc/ufw/before.rules 

At the beginning of the file:

```

*nat
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 10.1.123.0/24 -o eth0 -j MASQUERADE

:PREROUTING ACCEPT [0:0]
-A PREROUTING -p tcp -i eth0 --dport 2222 -j DNAT --to-destination 10.1.123.2:22
-A PREROUTING -p udp -i eth0 --dport 2222 -j DNAT --to-destination 10.1.123.2:22
# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

...

```

And at the end of the *filter:
```

...
# Let anything going via the private VPN subnet flow unrestricted
-A ufw-before-input -i openvpnbr0 -j ACCEPT
-A ufw-before-forward -i openvpnbr0 -j ACCEPT

# Forward port 2222 to 10.xxx.xxx.20 port 22
-A ufw-before-forward -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -m state --state NEW -i eth0 -d 10.1.123.2 -p tcp --dport 22 -j ACCEPT

# don't delete the 'COMMIT' line or these rules won't be processed
-A ufw-before-input -i tap+ -j ACCEPT
-A ufw-before-output -i tap+ -j ACCEPT
-A ufw-before-forward -s 10.1.123.0/24 -j ACCEPT
-A ufw-before-forward -d 10.1.123.0/24 -j ACCEPT

COMMIT

```

I know the second piece can be cleaned up a bit, many of those rules are either redundant or can be removed all together, it was just all due to my troubleshooting prior.

Also, the output of # ufw status verbose
```

Status: active
Logging: on (high)
Default: deny (incoming), allow (outgoing)
New profiles: skip

22                         ALLOW IN    Anywhere
80                         ALLOW IN    Anywhere
443                        ALLOW IN    Anywhere
1194                       ALLOW IN    Anywhere
10.1.123.0/24              ALLOW IN    10.1.123.0/24
8080                       ALLOW IN    Anywhere
2222                       ALLOW IN    Anywhere
22/tcp                     ALLOW IN    10.1.123.2

```

I have tried both Ubuntu 12.04 LTS and Debian stable, and while I am on Linode which provides their own kernel on Xen, they also provide an option to use your own, which I used the latest kernel for Ubuntu on 12.04, so I ruled out the possibility that it could be a missing compile option in the kernel. Thanks for your help in advance!

---

### Post by Tylerjd on 2013-01-02
I seem to have fixed the problem. After running netstat and seeing that a lot of connections were in the SYN_RECV state, I figured that they were not getting outbound for some reason. I verified the firewall was allowing them outbound, so I then looked at the actual OpenVPN connection. It occurred to me that it may not be able to route to the public internet without the client redirecting its traffic over the OpenVPN bridge, and once I put in the client.conf a directive to redirect the default gateway, it magically started working.

---

