---
title: "Help with route/iptables SNAT config"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by wdaniels on 2010-11-18
Hi, I'm trying to set up routing on a server so that it will send all traffic destined for a particular subnet via another server that will rewrite the source IP to pretend the traffic came from itself. The situation is basically that I have a particular service which only accepts traffic from a designated IP address, but I want actually to be able to route traffic also from other servers through the server with the authorised IP.

So I tried this...

For the origin host (non-authorised ip):

```
route add auth.server.ip.address dev eth0
route add -net target.subnet.address.0/24 gw auth.server.ip.address
```

*What I am expecting this to do is forward packets for the target subnet to the authorised server. So then, on the authorised server, I did:*

```
iptables -t nat -A POSTROUTING -s origin.server.ip.address -d target.subnet.address.0/24 -o eth0 -j SNAT --to auth.server.ip.address
```

*What I am expecting this to do is masquerade traffic coming from origin.server.ip.address that is destined for target.subnet to look like it comes from auth.server.ip.address.*

Make sense? It does to me, only it doesn't appear to work :D Unfortunately, I'm more of a programmer than a sysadmin and networking always makes me want to boil my head :@

It would be great if some kind soul would tell me what I'm doing wrong! As far as I can tell, the route on the origin server isn't even working...certainly if I try traceroute to the target subnet I only see one hop to the local host, not to the gateway server. But I don't even know if traceroute should show that anyway!

I probably lack some basic understanding of how these things work, though I always thought I was OK on the theory to be honest :D Any help greatly appreciated.

---

### Post by SeijiSensei on 2010-11-19
If "cat /proc/sys/net/ipv4/ip_forward" returns zero, your kernel doesn't allow forwarding of packets between interfaces.  (This is pretty much the standard on most distributions these days for security reasons.)  Try running "echo '1' > /proc/sys/net/ipv4/ip_forward" on the machine doing the routing and see if that fixes your problem.  Then change the entry for net.ipv4.ip_forward to one in /etc/sysctl.conf to make this change permanent.

---

### Post by wdaniels on 2010-11-19
> **SeijiSensei said:**
> If "cat /proc/sys/net/ipv4/ip_forward" returns zero, your kernel doesn't allow forwarding of packets between interfaces.  (This is pretty much the standard on most distributions these days for security reasons.)  Try running "echo '1' > /proc/sys/net/ipv4/ip_forward" on the machine doing the routing and see if that fixes your problem.  Then change the entry for net.ipv4.ip_forward to one in /etc/sysctl.conf to make this change permanent.

Hi, thanks for your reply, I had indeed forgotten about this setting! But unfortunately it still doesn't work :(

What tools do people normally use to debug these things? Is there anything that will show me the packets coming in and out of an interface so I can see exactly where they are going?

---

### Post by wdaniels on 2010-11-19
I should probably mention also that the origin server is actually a VPS running with KVM/QEMU configured for bridged networking, although the bridge seems to work fine for all other traffic and the gateway is a public IP that is reachable from the VPS.

Which reminds me...now that I have enabled forwarding on the gateway server, do I need to add some firewall rules to stop it forwarding other traffic or will iptables only forward for the rules that are set up?

Anyway, I am assuming I wouldn't need any special rules on the VPS host since the packets leaving the bridge should already be destined for the gateway IP, yes? And the SNAT rule on the gateway should keep track of the connection and translate the destination back to the IP of the VPS automatically for the response traffic?

---

### Post by SeijiSensei on 2010-11-19
I never use bridging so this may be off-target, but, since the guest and host share the same IP, how do you ensure that traffic is going to the right one?

As for your more general question about forwarding, that depends on your default iptables policies and whatever rules you've written governing the FORWARD chain.  If the default for forwarding is ACCEPT, then you'll need to add a REJECT rule at the bottom of the chain to block forwarding.  You can look at the INPUT/FORWARD/OUTPUT rules with "sudo ipchains -L -nv" and the rules for other tables like nat with "sudo iptables -t nat -L -nv".

---

### Post by wdaniels on 2010-11-19
> **SeijiSensei said:**
> I never use bridging so this may be off-target, but, since the guest and host share the same IP, how do you ensure that traffic is going to the right one?

No, they have different public IP addresses. The host is configured to send traffic for the VPS IP to the interface that is the host side of a tun/tap bridge (device "kvm" below), so that just comes out the other side on eth0 of the VPS (AFAIK :D).

The iptables rules for that are handled automatically by libvirt and all seems to be working OK. I don't see anything in the iptables rules on the host that I think would cause a problem:

```
root@vpshost:~# iptables -L -nv
Chain INPUT (policy ACCEPT 13M packets, 12G bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2253  147K ACCEPT     udp  --  kvm    *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
    0     0 ACCEPT     tcp  --  kvm    *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
  436  143K ACCEPT     udp  --  kvm    *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
    0     0 ACCEPT     tcp  --  kvm    *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 569K  110M ACCEPT     all  --  *      kvm     0.0.0.0/0            subnet.for.vps.0/24      
 478K  133M ACCEPT     all  --  kvm    *       subnet.for.vps.0/24       0.0.0.0/0           
    0     0 ACCEPT     all  --  kvm    kvm     0.0.0.0/0            0.0.0.0/0           
    0     0 REJECT     all  --  *      kvm     0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
    0     0 REJECT     all  --  kvm    *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT 12M packets, 16G bytes)
 pkts bytes target     prot opt in     out     source               destination
```

> **SeijiSensei said:**
> As for your more general question about forwarding, that depends on your default iptables policies and whatever rules you've written governing the FORWARD chain.  If the default for forwarding is ACCEPT, then you'll need to add a REJECT rule at the bottom of the chain to block forwarding.  You can look at the INPUT/FORWARD/OUTPUT rules with "sudo ipchains -L -nv" and the rules for other tables like nat with "sudo iptables -t nat -L -nv".

On the gateway (although I'm not conviced the traffic is even getting this far):

```
root@gateway:~# cat /proc/sys/net/ipv4/ip_forward
1
```

```
root@gateway:~# iptables -L -nv
Chain INPUT (policy ACCEPT 329K packets, 117M bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 444K packets, 194M bytes)
 pkts bytes target     prot opt in     out     source               destination
```

I can see here that I have to add a REJECT at the end of the FORWARD chain like you said. I'll wait until I have the rest of it working though so as to avoid adding more variables.

The rule in the NAT table looks like how I think it should look:

```
root@gateway:~# iptables -t nat -L -nv
Chain PREROUTING (policy ACCEPT 21004 packets, 1742K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 156K packets, 28M bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 SNAT       all  --  *      eth0    ip.of.the.vps        target.subnet.ip.0/24      to:this.host.public.ip

Chain OUTPUT (policy ACCEPT 156K packets, 28M bytes)
 pkts bytes target     prot opt in     out     source               destination
```

The VPS is actually running CentOS, though I don't expect that would be pertinent to my problem. The kernel routing table is this:

```
[root@vps ~]# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ip.of.the.gateway   0.0.0.0         255.255.255.255 UH    0      0        0 eth0
this.vps.subnet.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
target.ip.subnet.0     ip.of.the.gateway   255.255.255.0   UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         ip.for.host.bridge   0.0.0.0         UG    0      0        0 eth0
```

I have no idea what 169.254.0.0 is actually, but it seems to be one of those "special" subnets so I just ignored it.

PS: I really appreciate any help me with this, I'm a long way out of my comfort zone when it comes to iptables.

---

### Post by wdaniels on 2010-11-19
Ah, maybe there is something here...

```
[root@vps ~]# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
ip.of.the.gateway   0.0.0.0         255.255.255.255 UH    0      0        0 eth0
this.vps.subnet.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
target.ip.subnet.0     ip.of.the.gateway   255.255.255.0   UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         ip.for.host.bridge   0.0.0.0         UG    0      0        0 eth0
```

This last line:

```
0.0.0.0         ip.for.host.bridge   0.0.0.0         UG    0      0        0 eth0
```

I didn't realise it was set up quite like that. So all the traffic is sent to the IP of the host's bridge interface? And I just set a different gateway for my target subnet! I guess I have to change the gateway on the host instead of on the vps?

Will try it...

---

### Post by wdaniels on 2010-11-19
> **wdaniels said:**
> Will try it...

Well at least I'm getting a reply from the target now, but still not via the gateway that I set. If I traceroute from the VPS I see it hit the IP of the "bridge" interface but not the gateway. Even if I traceroute directly on the VPS host machine it's not hitting the gateway, even though the routing table looks correct:

```
root@vpshost:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
the.gateway.ip.address   0.0.0.0         255.255.255.255 UH    0      0        0 eth0
the.vps.ip.address   0.0.0.0         255.255.255.255 UH    0      0        0 kvm
host.public.subnet.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0.myvlan
vps.public.subnet.0     0.0.0.0         255.255.255.0   U     0      0        0 kvm
target.ip.subnet.0     my.gateway.ip.address   255.255.255.0   UG    0      0        0 eth0
0.0.0.0         this.host.public.ip 0.0.0.0         UG    100    0        0 eth0
```

There seems to be some things about my configuration that are not how I believed them to be. I don't think I 100% understand what libvirt is doing on the network side now for starters :(

Did I mention I hate networking? :D

Someone please help me :'(

---

### Post by wdaniels on 2010-11-19
I think my "kvm" interface on the host is more like a virtual switch than a tun/tap bridge, which is what I thought it was.

There is another interface on the host called "vnet0" which gets added only when the VPS starts, so I suppose that must be the bridge interface, and those FORWARD rules in the host iptables are just moving any traffic to/from the VPS subnet through the QEMU switch "kvm"? Maybe that bypasses the kernel routing table or something? Maybe I should add a FORWARD rule to send traffic from the VPS IP destined for my target subnet via my gateway.

I'm not too sure where the kernel routing table/iptables begin and end. I did think that iptables must work on top of the routing table :S

I expect I'm just talking misguided gobbledygook to myself at this point, but it seems to help me think it through so I'll continue if nobody minds :D If anybody is still reading this and does happen to know anything about it all, please do say!

---

### Post by wdaniels on 2010-11-19
I just discovered the wonderful tcpdump :)
So forget the KVM bridge stuff...my route doesn't even work directly on the host.

If I "tcpdump src my.vps.host.ip" on the gateway and then ping the gateway directly from the VPS host, I see the network packet in tcpdump. But pinging an IP in my target subnet for which I added that gateway, it just goes directly instead (an API I'm calling in the target subnet reports the real IP of the VPS host machine and nothing is shown in tcpdump on the gateway).

The route is shown correctly on the VPS host when I use "route -n", and I have tried it both with the whole subnet and just a single host in the target network (i.e. so that it is first in the table), but on no occasion has my VPS host sent a packet for that network via the specified gateway.

So what could cause my route not to work? Surely I don't have to NAT the source & destination IPs using iptables in both directions to get it to go via the gateway? Any ideas?

---

