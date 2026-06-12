---
title: "Can't ssh in when using ppp0 as interface"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by bzkt on 2009-11-25
Hello, I have a server at home that I run Ubuntu 9.10 on. This server is going to use a pptp-connection (ppp0) and routing all traffic through it.

So far I've set up the connection and made a script for ip-up that adds a route for it.
```
route add default dev ppp0
```
This works without any problem and all my traffic gets routed through the pptp-connection.

My problem is that I can't ssh to the server when the pptp-connection is enabled. I can ssh to the servers local and external ip when it's not using it, but when I use it I can't ssh to the external ip. I can ping the external ip but when I try to ssh I just get a time out.

ssh -v <myuser>@<external ip for ppp0> just outputs that it times out. I've tried to connect from another remote linux server as well. If I ssh to the local ip and connects to the server from the server itself using the external ip for ppp0 it works.

I've also tried tcpdump for ppp0 but ended up with nothing, I got ouput when I used ping but not ssh. There is no configuration problem with my router, I don't have any iptables-rules set up and I have looked in hosts_allow and hosts_deny.

My routes:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
188.126.80.0    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
80.67.2.69      192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
80.67.2.68      192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
80.67.2.70      192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

Just to clarify:
laptop ssh -> server local ip: works
laptop ssh -> server external ip (eth0): works
**laptop ssh -> server external ip (ppp0): doesn't work**
server ssh -> server external ip (ppp0): works

Would really appreciate some help!

---

### Post by Lars Noodén on 2009-11-26
"I got ouput when I used ping but not ssh."

Incoming ping?  That is ping from the outside machine A to the machine your sshd is running on C?

```

+-----+                  +------+
|     |  inet      vpn   |      |
|     A ------ B ======= C      |
| ssh |                  | sshd | 
+-----+                  +------+

```

Also, at this early stage, if you are setting up a vpn, it might be wise to avoid PPTP and investigate IPsec instead.

---

### Post by bzkt on 2009-11-26
> **Lars Noodén said:**
> Incoming ping?  That is ping from the outside machine A to the machine your sshd is running on C?
Almost. My setup is like this:

```

+-----+                          
|     |                          
|     A ----|                    
| ssh |     |                     
+-----+     |                     
            |                                
            |-------- Router ------- (inet) ======= VPN
            |    
+----- +    |
|      |    |
|      B ---|
| sshd |
+------+
```
The VPN-service is not mine so I can't control it and it runs PPTP.

---

### Post by Lars Noodén on 2009-11-27
If B is running a VPN client and the symptoms occur when that is active, then it sounds like it might be a routing problem.  I am too much of a novice with routing to be sure of a solution.   VPNs tend to grab all traffic and the absence of data from tcpdump suggests that is happening. 

What about traceroute, and traceroute using TCP to port 22?
[indent]
traceroute -nFT -p 22 *xx.yy.zz.B*
[/indent]

Can you connect (or someone test the connection) to sshd on B from VPN?

You want the traffic for your LAN, at least, going through your router.  Are you wanting to access only a few machines via the VPN and using eth0 for the rest of the world or accessing everything.


Try adding least an alias ip address for eth0 and using multiple **ListenAddress** directives in sshd_config.  (As usual, make a copy first so that restoring the last known good version is as easy as **cp *sshd_config.orig* *sshd_config***)

---

