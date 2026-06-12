---
title: "Computers in VPN can't see each other"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by d3ngar on 2011-04-02
Hi,

I have set-up an Ubuntu VPN server in my home. 

My goal is to have my office computer (currently here, also Ubuntu) connect to the VPN and I would then be able to jump off this client into my office network. Well, the later part would probably see me VNC to the office-client and then use the computer as if I was sitting in front of it.

I have already got the VPN connection going from the Server and two client computers in another network to play around with. I have am able to connect to the VPN from both clients fine, no problem.

**My problem:** The two clients can't see each other.

I assume I have to set some routing...

**In short:** How can two VPN clients see and communicate with each other when connected to the host?

[I set up the VPN according to this guide]("http://home.inestdia.com/localserver/setupapptpvpnserverubuntuathome").

Thanks for your help.

Chris

---

### Post by d3ngar on 2011-04-02
Update: I think what's causing the issue on the host is this:

```

cat /proc/sys/net/ipv4/ip_forward
0

```

I thought I could change that in the /etc/sysctl.conf, but this might require restarting. I will try that and report back.

---

### Post by d3ngar on 2011-04-03
Bumping this thread as it remains an issue...

---

### Post by d3ngar on 2011-04-03
Okay, I got it solved...

The issue had to do with routing and I was able to fix it by applying manual routing.

Initially, only this IP I got was scanned for on the server side:

```
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
86.171.76.70    192.168.1.254   255.255.255.255 UGH   0      0        0 wlan0
86.171.76.70    192.168.1.254   255.255.255.255 UGH   0      0        0 wlan0
10.10.10.1      0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0

```

But then, I simply added a manual route:
```
~$ sudo route add -net 10.10.10.0 netmask 255.255.255.0 dev ppp0

```
which added:
```
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
86.171.76.70    192.168.1.254   255.255.255.255 UGH   0      0        0 wlan0
86.171.76.70    192.168.1.254   255.255.255.255 UGH   0      0        0 wlan0
10.10.10.1      0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
10.10.10.0      0.0.0.0         255.255.255.0   U     0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0

```

---

