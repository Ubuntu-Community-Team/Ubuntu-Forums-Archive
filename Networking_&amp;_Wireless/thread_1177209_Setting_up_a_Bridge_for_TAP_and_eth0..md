---
title: "Setting up a Bridge for TAP and eth0."
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by Crafty Kisses on 2009-06-03
Well my main focus was to create a network bridge from **br0, tap0 to eth0**. It's basically going to route any packets to the ethernet devices that are currently in use. Now usually I would be able to route the packets from tap0 to eth0 just fine. But now when I try to route any packets to tap, I get the following:
```
Received packet with own address as source address
```
Now for me to route these packets correctly to tap, I had to set iptables up like this:
```
iptables -A INPUT -i tap0 -j ACCEPT
iptables -A INPUT -i br0 -j ACCEPT
iptables -A FORWARD -i br0 -j ACCEPT
iptables -A FORWARD -i br1 -j ACCEPT
```
Then from there I added a host route, for the simple fact that it's obviously required in order for this routing process to work correctly, because without this to my knowledge the packets wouldn't route to tap, so I ran:
```
route add -host 192.168.1.254 dev tap0
```
Then did something similar for the bridge, I ran:
```
route add -host 192.168.11.200 gw 192.168.1.1 dev br0
```
Then to confirm this, I just wanted to make sure IP forwarding is enabled, so I can do this. So I finally run:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
Then I try this process again, I get an error, but it's not the same error as before, I didn't get the routing error but even a stranger error, which is:
```
Can't add **tap0** to bridge eth0: Operation not supported
```
Before anyone asks, yes I do have tunctl installed, I compiled it from source, so I'm not sure if that's the problem, but I got it from the [official website]("http://tunctl.sourceforge.net/"). I also made sure that the bridge configuration is correct, I would obviously do this, the main line that could be an issue is:
```
bridge_br0=( "eth0" "tap0" )
```
Now if that's wrong someone please tell me, but that should be working just fine. If that's wrong I'll be glad if you can correct me on that, maybe that can get these annoying errors sorted out. I'd also like to state the **IP chains** look pretty normal as well, I mean they don't look out of the ordinary, take a look yourself:
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere
    0     0 ACCEPT     udp  --  ath0   any     anywhere             anywhere            
```
So if ruled out a couple of potential issues which are now, IP chains config, forwarding options, bridge/tap configurations and setup. So I'm not really sure what it could be at this point. I mean it should be working but it's still giving me those two errors and they are alternating. So I'm not sure what's going on.

---

