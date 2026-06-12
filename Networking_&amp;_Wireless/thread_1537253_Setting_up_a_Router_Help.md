---
title: "Setting up a Router Help"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by linux1534 on 2010-07-23
Hi,

I tried to setup a Ubuntu Wired Router according to the manual but found a problem.

At the end of the doc page it says:
```

auto br0
iface br0 inet static
    address 192.168.0.1
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
    bridge-ports eth1 wlan0
```The problem though is that I don't have a wireless connection and what do I put at the end?

It says "bridge-ports eth1 wlan0" so should I change that to "eth1" twice or just leave "wlan0" out or how do I fix this?


Thanks.

---

### Post by linux1534 on 2010-07-23
Anyone... pls.

I tried leaving it out btw but it didn't work.

---

### Post by trundlenut on 2010-07-23
you do have two network cards in your machine don't you?

Assuming this then you need to put in whatever your second connection is eth2 for example or perhaps eth0.

---

### Post by linux1534 on 2010-07-23
Yes of course, thanks for replying.

I have two network cards, eth0 and eth1.

eth0 is external/internet and eth1 is internal to the hub.

---

### Post by trundlenut on 2010-07-23
Then I'm assuming that the last line wants to read:

```
bridge-ports eth0 eth1
```

---

### Post by linux1534 on 2010-07-23
Nope that doesn't work.

Only this works having internet on the same machine.

```

bridge-ports eth1

```

---

### Post by trundlenut on 2010-07-23
what does the rest of the interface file look like?

---

### Post by linux1534 on 2010-07-23
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet static
#address 192.168.10.1
#network 192.168.10.1
#netmask 255.255.255.0
#broadcast 192.168.10.255

auto br0
iface br0 inet static
address 192.168.10.1
network 192.168.10.1
netmask 255.255.255.0
broadcast 192.168.10.255
bridge-ports eth1

```

I tried uncommenting eth eth1 and commented out.

---

### Post by trundlenut on 2010-07-23
what exactly is the problem? What doesn't work when you use bridge-ports eth0 eth1 ?

Can you access/ping the router from your internal network?
Does the router have a connection to the internet? - Can you ping something outside from the router?

---

### Post by linux1534 on 2010-07-23
The problem is that it doesn't share internet, I wanna set it up as a router to share internet connection to the computers behind it.

I have internet on the router machine. I can ping the router machine from my internal machines but have no internet connection at them.

I set it up correctly, the internal machine, with an IP address, correct gateway and nameserver and all that. That all checks out. But no internet.

Could it be something else maybe? This is the correct way to use the setting up ubuntu as a Router right? Just to make sure.

---

### Post by trundlenut on 2010-07-23
could this be a firewall problem then, is it that data isn't being forwarded?

Have a look at [this how to]("http://ubuntulinuxhelp.com/how-to-setup-a-wireless-ubuntu-router/").

---

### Post by YesWeCan on 2010-07-23
> **linux1534 said:**
> The problem is that it doesn't share internet, I wanna set it up as a router to share internet connection to the computers behind it.

I have internet on the router machine. I can ping the router machine from my internal machines but have no internet connection at them.

I set it up correctly, the internal machine, with an IP address, correct gateway and nameserver and all that. That all checks out. But no internet.

Could it be something else maybe? This is the correct way to use the setting up ubuntu as a Router right? Just to make sure.
Hi there. I think you may be confusing a router with a bridge and you may have misunderstood that guide. What you want to do is a sort of bridge in normal English but is not a bridge at all in networking terminology.

A bridge connects two LANs as if by physical link as if all the PCs are on the same LAN. But some are on one logical subnet and the others are on a different logical subnet. A PC's NIC cannot send packets to a PC on a different logical subnet. One of your subnets is eth1 192.168.10.0/25; you haven't said what the other subnet is for eth0. When PCs are on exclusive subnets they cannot communicate with one another even though the physical LANs are bridged.

A router is not a bridge. A router is a gateway which is a special type of relay that forwards packets from one subnet to another. It also has to do something called SNAT or MASQUERADE so that replies get routed back to the originating PC.

So remove the bridge directive in your interfaces config.

Hint: you need to use 'iptables'. You also need to enable IP forwarding in your linux kernel. Just search this forum for configuring a router - there are lots of guides. :)

---

### Post by YesWeCan on 2010-07-23
> **trundlenut said:**
> could this be a firewall problem then, is it that data isn't being forwarded?

Have a look at [this how to]("http://ubuntulinuxhelp.com/how-to-setup-a-wireless-ubuntu-router/").
Yes this is a firewall problem in the sense that iptables is used for creating a firewall. But it is more correctly the absence of Network Address Translation (NAT) rather than a firewall preventing the forwarding. Assuming, that is, that a firewall has not been set up. If a firewall has been set up then a "hole" in the wall is required as well as a SNAT (source NAT) or a masquerade (a more versatile type of SNAT).

If no firewall is set up (default state of Ubuntu after install) then only two things are needed: a SNAT rule in iptables and the enabling of IP forwarding in the kernel.

In the how-to you cite they are doing two things - a bridge of a wireless NIC and a wired NIC and they are setting up a router. I think the OP just needs the router bit.

---

### Post by linux1534 on 2010-07-23
Yes the router is so that I can connect it to my hub and connect other computers to it rather than straight from my modem into my hub which isn't possible, thats why I have my router machine to "share connection".

And no I don't have a firewall running or whatsoever.

So you want me to remove the bridge? This is like the whole point of it isn't it, if I remove it than nothings left. :)
I know the masquerading except I wanna try it this way to start off, see if it works.

---

### Post by YesWeCan on 2010-07-23
[QUOTE=linux1534]The problem though is that I don't have a wireless connection and what do I put at the end?[/QUOTE]
That's the clue. You are not trying to bridge a wireless lan with your wired lan. A bridge merges two lans. It does not do routing. Merging is not the same as routing.

My understanding is that you want eth1 packets that are addressed to the internet to be routed through your linux box to the gateway on eth0. This is nothing to do with bridging. You do not want to bridge anything.

You may be thinking if you bridge eth0 with eth1 then clients on eth1 can use the eth0 gateway? No. Not unless eth0 and eth1 use the same subnets. This is because a client on subnet A cannot send packets to the gateway on subnet B, even it you have bridged the two subnets. This is how subnetting works. In order to cause packets to be relayed from subnet A to subnet B you need a router. The router function is the combination of FORWARD and MASQUERADE rules. Iptables forwards everything by default so you don't need any FORWARD rules.

Does that make sense?

---

### Post by linux1534 on 2010-07-23
Oh yea, I get it. Unfortunately though. :(

I thought it would configure ubuntu to act as my alike a D-Link etc physical router and with the bridging just connect eth0 and eth1 to act that way exactly being able to connect eth1 to my hub and so share internet.
But I guess not, that is too bad. :)


EDIT: I'm currently trying to get the MASQUERADING to work.

Already got it working, I'm good. :)


Thanks for the help.

---

