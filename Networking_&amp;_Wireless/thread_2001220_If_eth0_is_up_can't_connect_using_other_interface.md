---
title: "If eth0 is up can't connect using other interface"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by N0mada on 2012-06-10
Hi all,

there are 2 interfaces in the box:
ppp0 (a HUAWEI USB broadband) "external IP"
eth0 "internal IP"

i have set up vino-server, sshd, etc.

if both interfaces are up i only can connect using eth0.
if i down eth0 i can access all services (VNC; ssh, etc.) using external IP with no problems,
but if now i up eth0 actual connection (using ppp0) is lost.

I would appreciate any help you can offer. 
TIA !

---

### Post by dandnsmith on 2012-06-12
if you post the results of 
ifconfig
route
it might give a clue as to what is happening.
Please post the route results with eth0 both up and down.

---

### Post by efflandt on 2012-06-12
You are not setting a default gateway on eth0 are you?  There should only be a default route on one device, typically the one that leads to the internet (on ppp0 to your ISP's gateway).  If there is more than one default gateway, the first one in the routing table (w/flags UG) is followed (which may block the default route through ppp0)

There should be no routing or gateway set on eth0 in your case unless you have network specific local routing to a local gateway to another LAN.  No gateway is needed on eth0 to access the same LAN as eth0.

---

### Post by N0mada on 2012-06-14
Thanks efflandt, that fixed the problem.

The route table in three cases is:

1) Only ppp0 Active
0.0.0.0         10.64.64.64     0.0.0.0               UG    0      0        0 ppp0
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

2) ppp0 + eth0 Active (eth0 WITH default Gateway)
0.0.0.0         192.168.1.1     0.0.0.0               UG    0      0        0 eth0
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0        U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0     U     1      0        0 eth0

3) ppp0 + eth0 Active (eth0 WITHOUT default Gateway)
0.0.0.0         10.64.64.64     0.0.0.0               UG    0      0        0 ppp0
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0         U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0     U     1      0        0 eth0

Anyway i have a doubt...

Both interfaces having assigned default GW are capable to send/receive traffic to/from the Client.
(lets suppose just one active at a time)

IPCli ---- INET ------ IPExt(ppp0) -|Linux BOX|-IPInt(eth0) ---Router-----INET--|
                                                                                                                |
       <----------------------------------------------------------------------------------|

I understand the first default gateway is followed by the outbound  traffic, but why the connection is lost in the CLI?, i mean, why just  the traffic can´t return to Cli following a different path for outboud  traffic. inbound traffic is received by ppp0 and outboud traffic is  routed trough the routed in the LAN.
Is this possible such a "loop" ?
Internet Routers in beetween switch routes very often...

I know this is not the original subject, but i prefer to understand all of this rather than just fixing it, if u dont mind.

Thanks!

---

### Post by SeijiSensei on 2012-06-14
> i mean, why just the traffic can´t return to Cli following a different path for outboud traffic.

Because the remote machine will send the return packets back over the route by which they arrived.

---

### Post by N0mada on 2012-06-14
> **SeijiSensei said:**
> Because the remote machine will send the return packets back over the route by which they arrived.

But if the remote machine already knows the route (same route as input packets) there is no need to check a routing table *theoretically*  and the traffic in ppp0 would reach the local machine by using ppp0 as GW (same output route/GW as input route/GW) even if routing table tells to output using eth0. (Case 2).

I thougt routing table is just "my next jump" to reach the final IP (originating IP if i am the server sending back traffic to a client). I deliver the packets to the interface i´ve been told to by the routing table and i have finished my responsability in the chain.

Where i can read about this in deep ? because what i expect and what really happens aren't the same thing ](*,)

---

