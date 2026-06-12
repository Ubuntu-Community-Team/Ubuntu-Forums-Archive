---
title: "SSH VPN tunnel not working"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by MikeRose.Aus on 2011-03-14
Hey guys, I realise this topic is fairly heavy for a forum like this, so please bear with me.

The setup:
3 computers, hostA, hostB and hostC. hostB is a router (in a sense) and hostC is behind it. I have root access to hostA and hostC but only user access to hostB. I am not permitted to open any ports on hostB. I am not permitted to initiate any connections 'out' of hostB to the internet (but can connect inwards to hostC). hostC cannot make or receive any connections to/from the internet.  (Classic restrictive firewall/proxy scenario)


The challenge: Route all hostC's traffic via a ssh tunnel to hostA.


Here's what I've done:

Open a SSH port forward to hostC:
hostA$ ssh -f -N -L 127.0.0.1:12345:hostC:22 hostB

Open a SSH tunnel to hostC (via the port forward above)
hostA$ sudo ssh -f -N -w 0:0 -p 12345 root@127.0.0.1

Set up the end points of the tunnel:
hostA$ sudo ifconfig tun0 192.168.0.1 pointopoint 192.168.0.2
hostC$ sudo ifconfig tun0 192.168.0.2 pointopoint 192.168.0.1

Now, according to all common lore on the internet, I should be able to ping through the tunnel fine.

hostA$ ping 192.168.0.2

But all packets are dropped. Likewise for the other direction. Packets *are* registering as Rx and Tx on the tun0 interface when I take a look at ifconfig though. The routing tables have been automatically updated by ifconfig to provide the point-to-point link via tun0 so I doubt it's a routing issue.

I thought perhaps it was just a problem with ICMP over tunnels or something (in hindsight that doesn't really make sense) so I pushed ahead with adding the extra routing rules and IP forwarding:

Set IP forwarding and NAT:
hostA$ echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
hostA$ sudo iptables -A FORWARD -o eth0 -i tun0 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
hostA$ sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
hostA$ sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

Add routing information:
hostC$ sudo route add hostA gw hostB
hostC$ sudo route add default gw 192.168.0.1

The routing doesn't work. It would seem that the earlier ICMP connectivity problem is for everything.


I'm so close! I can taste freedom! Where am I going wrong?

Cheers,
Mike


P.S. before any smart alec comes in with 'SSH tunnel over SSH port forward will be super slow!!!!!!!':
1. I am aware that both encapsulating TCP and IP headers multiple times will be a source of network overhead.
2. I am aware that multiple SSH encryption layers will be a source of CPU overhead.
3. I'm still doing it.

P.P.S. Please don't give me 'why don't you do X?'. I've looked at alternative solutions. Questions about my choice of implementation are going to decrease the signal to noise ratio for this thread.

P.P.P.S. I apologise if the two post scripts above make me seem arrogant. I'm really not! Promise! :)

---

