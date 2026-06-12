---
title: "Static IP addresses not working without switch"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by servern00b on 2012-04-02
Hi everyone,

I got the following situation: I have 3 machines: a server, a workstation and a laptop. The server runs ubuntu 12.04 and the other two various versions of kubuntu.
I want the server to have static IP addresses, so this is what i put in /etc/network/interfaces

```

auto lo
iface lo inet loopback

autho eth0 eth1

iface eth0 inet static
  address 192.168.0.5
  network 192.168.0.0
  netmask 255.255.255.0
  broadcast 192.168.0.255

iface eth1 inet static
  address 192.168.0.6
  [rest like eth0]
```ifconfig tells me now, that both NICs are UP and are assigned to the above IPs. Fine.

Now I plug the server into the router, and the workstation too. The server addresses are outside the routers designated DHCP section, so the  workstation is assigned an IP address like 192.168.0.101, no collisions. Fine.

Now all is well, I can ping, SSH into the server, and I can access the samba shares from the workstation.
The only problem is, the router is only 100MBit, whereas the computers all have GBit network cards. The server is new and there's TBs of data all over the place I want on the server and that would take weeks.
So plug the server's first NIC directly into the workstation, make sure it has an IP on the same subnet via

root@workstation# ifconfig eth0 inet 192.168.0.10

and try to ping the server. => Destination Host Unreachable :(
both interfaces are reported up and running  by ifconfig. When I plug the workstation into the laptop instead (which normally also uses DHCP to handle its eth0) and give it an IP on the subnet

root@laptop# ifconfig eth0 inet 192.168.0.11

I instantly have a working connection. So the problem can't be with any hardware or cables (I tried various crossover and non-crossover cables). There are no routes out of the subnet involved, so there should be no need for any gateway etc. as far as I can understand it.

Anyone any ideas where the problem is?

---

### Post by dandnsmith on 2012-04-03
I think it's a routing problem, and when you plug the workstation into the laptop each of them has only one place to send the traffic so there is no room for confusion.

Now have a look at the routes which are set for your workstation plugged directly to server - I'm willing to bet that the packets from the server all go to the router, instead of those for the workstation going to the direct interface.

Post the output from this setup with the *route* command?

---

### Post by praseodym on 2012-04-03
> aut[COLOR="Red"]h[/COLOR]o eth0 eth1
Typo?

---

### Post by Iowan on 2012-04-03
Having both interfaces in the same subnet violates the Spanning Tree Protocol.
You can check **route -n** to see which interface is used as the gateway (hopefully not both).
(Try it with **sudo** if that doesn't work...)

---

### Post by servern00b on 2012-04-04
@praseodym: yeah typo ;) in the actual file it read "auto" like it should.

As to the output of "route". First the server, this one doesn't change during all the plugging and unplugging:
```

Kernel IP routing table
Destination   Gateway  Genmask          Flags   Metric    Ref    Use    Iface
192.168.0.0   *        255.255.255.0    U       0         0        0    eth1
192.168.0.0   *        255.255.255.0    U       0         0        0    eth0

```Now the workstation, while connected to the router (which has ip 192.168.0.1):
```

Kernel IP routing table
Destination   Gateway        Genmask        Flags  Metric  Ref    Use  Iface
default       192.168.0.1    0.0.0.0        UG     0       0      0    eth0
link-loca     *              255.255.0.0    U      1000    0      0    eth0
192.168.0.0   *              255.255.255.0  U      1       0      0    eth0

```When  I connect the workstation directly to the server, and give it an IP  address on the subnet manually, route shows only this now:

```

Kernel IP routing table
Destination   Gateway  Genmask         Flags  Metric  Ref  Use  Iface
192.168.0.0   *        255.255.255.0   U      0       0      0  eth0

```When then connected to the laptop instead of the server,  it stays exactly the same. Also on the laptop route shows the exact same  line for the wired interface eth0 plus 3 more lines for the wireless  interface wlan0 that are very similar to the 3 lines the workstation  shows when connected to the router.
I have no idea, what the stuff beyond the netmask means :/

@Iowan: I also tried "route -n" that produces the exact same output but with all the asterisks replaced by 0.0.0.0

The server has a network activity light on the front panel. I **see** the ping packets hit when it's directly connected to the workstation and I ping it. Also ifconfig shows no dropped packets so proably you are right and it sends the answer to someone who just isn't there.

Ok, maybe someone with a stronger connection to the force than me can see the problem now?

---

### Post by dandnsmith on 2012-04-04
I'm not sure you can rely on this, but the non-working of workstation to server eth0 seems, to me, to be going to get all the replies on eth1 (as that is the first routing entry which satisfies the route) - so you never see the replies.

You need to change the routes so they aren't identical, and, even more important, separate the traffic sensibly with a regard to order of the entries in the routing table.

If I recall correctly, there is an option to save the routes over reboots via a route call - however, consulting the man page I don't see this, so it may be that it is only a Windows version parameter/property.

You'd be much better off if you put eth0 and eth1 on separate subnets - then you could avoid a lot of fiddling about.

---

### Post by spynappels on 2012-04-04
Hi,

Looking at your original post, what I did in that situation was get a small GbE switch and plug all my GbE equipped machines in to it, and then run a Cat5 from the switch to the router. All local traffic goes through GbE switch, and only traffic for the internet (or any nodes plugged directly into a 10/100 port on the router) will have to use a lower speed interface.

As for your specific problem, if you are determined you want both NICs on the server to have a 192.168.0.x IP address, you will have to make one interface the default route interface by adding a ```
gateway 192.168.0.1
``` line to it's entry in /etc/network/interfaces (e.g. eth0) and then creating a static route on the server to route all traffic to the required IP address at the other end of the direct connection through the other interface (eth1).

---

### Post by servern00b on 2012-04-05
Hey, thanks for all the answers!

So you made me think of some rather trivial things I didn't come up with myself:

1. I ifdown'ed eth1 and had a connection momentaryly (it definitely removed the route)
2. I plugged the workstation into eth1 instead of eth0 and also got my connection
3. I watched the activity lights when everything is plugged into the switch and both interfaces show activity when I ping eth0.

So, the routes really are the tip of the iceberg of the problem. My immediate problem is solved and I'm happe to have 3-times the throughput now.
This also explaines why the switch in the middle solves the problem: on  the server incoming transfer goes via eth0 and outgoing via eth1 and the  switch directs everything to the right place.

@spynappels: A GbE switch is definiteliy the next marker on the roadmap, but at the moment the server has eaten up all the budget ;)

And there's the thing right there: There are still more machines on the subnet than the 3 stated above and I want them all to see each other. So splitting the subnet would then require at least 2 switches which I think is overkill. What I want is to plug multiple clients into the switch, have them assigned IP addresses via DHCP and always find the server at a static IP address. Now to maximize network throughput I want to have full GbE access to the server from 2 different machines on the subnet, therefore the  two static IPs.
The spanning tree protocol assumes every machine to be a single node in the subnet with routers being special because they answer to a single IP address on multiple physical ports.

OK, so the real question is: [B]How do I configure a server to have two network interfaces on the same subnet?

[/B]If someone can give me a hint where to look for that I think we can close this thread. Thx everyone.

---

### Post by spynappels on 2012-04-05
Ok, you could always look at getting a (second-hand) switch which allows NIC teaming or bonding (link aggregation) and bond both NICs into 1 virtual connection with double the bandwidth into the switch, so each of the GbE clients should have access to it's full bandwidth.

I understand the budget constraints, but this would be a more standard way of doing what you want, and is not really that expensive.

Re the DHCP, if you plug your modem/router (which I presume is doing your DHCP) into the switch, anything else plugged into the switch will still be able to use it...

---

### Post by servern00b on 2012-04-05
@spynappels: Thx, **link aggregation** really was the keyword. I will try to get my hands on some LACP capable switch.

For anybody experiencing the same difficulties or having the same plan: the linux **bonding driver** found in the **ifenslave** package in ubuntu is your starting point. This will make one virtual network interface out of multiple physical ones providing load balancing as well as redundancy.

So, problem solved, thread closed :)

*Edit: *I found a howto page that was written for dapper but still works fine with precise: [https://help.ubuntu.com/community/LinkAggregation](https://help.ubuntu.com/community/LinkAggregation). Using mode=6 will not even require a special switch.

---

