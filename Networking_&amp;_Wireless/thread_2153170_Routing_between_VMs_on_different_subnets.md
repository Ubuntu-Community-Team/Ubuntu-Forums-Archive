---
title: "Routing between VMs on different subnets"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by vRouter on 2013-06-10
I am trying to setup Ubuntu 12.10 running in a VirtualBox 4.2.12 VM as a router between a number of VBox VMs running Win7. The VBox host OS is Win7.

My setup looks something like this:

```
                     ======================
                     ||     UbuntuVM     || 
-----               ------            ------                     -----
|VMa|---internal1---|Eth1|            |Eth3|----internal3--------|VMc|
-----               ------            ------                 |   -----
                     ||                  ||                  |
-----               ------               ||                  |   -----
|VMb|---internal2---|Eth2|               ||                  ----|VMd|
-----               ------               ||                      -----
                     ||                  ||
                     ======================


```

[U][B]UbuntuVM:
[/B][/U]Eth0: VBox bridged network. Will be used for SSH.
Eth1: VBox internal network ‘internal1’. IP: 192.168.100.2   Mask 255.255.255.0
Eth2: VBox internal network ‘internal2’. IP: 192.168.101.2   Mask 255.255.255.0
Eth3: VBox internal network ‘internal3’. IP: 192.168.10.2   Mask 255.255.255.0

[U][B]VMa:
[/B][/U]VM with Win7.
VBox internal network ‘internal1’. IP: 192.168.100.3   Mask 255.255.255.0
Should only be able to communicate with VMc and should use OpenVPN running in VMc for internet connection.

[U][B]VMb:
[/B][/U]VM with Win7.
VBox internal network ‘internal2’. IP: 192.168.101.3   Mask 255.255.255.0
Should only be able to communicate with VMd and should use OpenVPN running in VMd for internet connection.

[U][B]VMc:
[/B][/U]VM with Win7.
VBox internal network ‘internal3’. IP: 192.168.10.3   Mask 255.255.255.0
Manages VMa and provides internet connection for VMa via OpenVPN and a VBox Bridged networking adapter (not show).

[U][B]VMd:
[/B][/U]VM with Win7.
VBox internal network ‘internal3’. IP: 192.168.10.4   Mask 255.255.255.0
Manages VMb and provides internet connection for VMb via OpenVPN and a VBox Bridged adapter.

I can ping:
VMa <-> Eth1 (both directions)
VMb <-> Eth2 (both directions)
VMc <-> Eth3 (both directions)
VMd <-> Eth3 (both directions)

But I can NOT ping:
VMa <-> Eth3 or  VMa <-> VMc or VMc <-> Eth1
VMb <-> Eth3 or  VMb <-> VMd or VMd <-> Eth2

Looks like routing in UbuntuVM is not working.

On Ubuntu, sysctl -p returns "net.ipv4.ip_forward=1".

This is Ubuntu /etc/network/interfaces:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo eth0 eth1 eth2 eth3
iface lo inet loopback

iface eth0 inet static
address 10.0.0.200
netmask 255.255.255.0

iface eth1 inet static
address 192.168.100.2
netmask 255.255.255.0

iface eth2 inet static
address 192.168.101.2
netmask 255.255.255.0

iface eth3 inet static
address 192.168.10.2
netmask 255.255.255.0

```

~$ route gives this:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
192.168.10.0    *               255.255.255.0   U     0      0        0 eth3
192.168.100.0   *               255.255.255.0   U     0      0        0 eth1
192.168.101.0   *               255.255.255.0   U     0      0        0 eth2
```


I have not defined any rules for iptables.

Without the Ubuntu router, VMa can use the OpenVPN connection in VMc. But I have no way of controlling who or what VMa communicates with, which is what I need.

What should I do to make the routing VMa <-> VMc and VMb <-> VMd work?

---

### Post by The Cog on 2013-06-10
I would like to double-check that forwarding is enabled, with the command
```
cat /proc/sys/net/ipv4/ip_forward
```

You need to make sure that the other hosts know that the Ubuntu router is their default gateway (or that the route to the other networks is via the Ubuntu router). 

I would then use tcpdump to see what packets are (or not) being recieved/sent by the router from the hosts. Something like:
```
sudo tcpdump -np -i eth1
```

---

### Post by vRouter on 2013-06-10
OK, I have tinkered with routing and default gateways in VMa and VMc and have made some progress.

I set Eth1 as default gateway in VMa.

I also added a route in VMc which was missing (route add 192.168.100.0 mask 255.255.255.0 192.168.10.2)

And now I can actually ping VMa <-> VMc in both directions. :D

However, when the setup worked without the Ubuntu router, I had set VMc as default gateway in VMa. That way VMa would use the shared OpenVPN TAP adapter in VMc to reach internet.

But how do I do that now with the Ubuntu router between VMa and VMc?

I can't set VMc as default gateway in VMa, because that just gives me an error 'The route addition failed: Element not found', which is understandable.

If I could tell the Ubuntu router that everything coming in on Eth1 should be sent to VMc and everything coming in on Eth3 from VMc should be sent to VMa, then I believe it would work. But I don't know how to set such complicated routes (not even sure it is possible).

How can I get VMa to use VMc as it's default gateway now when the router is in the middle?

---

### Post by The Cog on 2013-06-10
> However, when the setup worked without the Ubuntu router, I had set VMc as default gateway in VMa. That way VMa would use the shared OpenVPN TAP adapter in VMc to reach internet.
I suspect that when they were on the same VLAN, VMa wasn't using the OpenVPN connection at all. I think it was probably just talking normally to VMc.
> But how do I do that now with the Ubuntu router between VMa and VMc?
VMa must have a route to VMc in order to be able to make the tunnel. But it must also use the tunnel as its default route. This line added to the client configuration file should do that by adding a specific route to the VPN server (VMc) and changing the default route as the tunnel comes up, which I think answers the rest of your questions:
```
redirect-gateway def1
```
The option is described here:
[http://openvpn.net/index.php/open-source/documentation/manuals/69-openvpn-21.html](http://openvpn.net/index.php/open-source/documentation/manuals/69-openvpn-21.html)

---

### Post by vRouter on 2013-06-10
> I suspect that when they were on the same VLAN, VMa wasn't using the OpenVPN connection at all. I think it was probably just talking normally to VMc.
But it did use the VPN connection to get out on internet. This was verified with traceroute. The communication between VMa and Vmc always was a normal connection, which is OK.

It used to work like this, and this is how I want it to work now if possible: When VMa communicates with the internet, the packet goes to VMc on a normal communication (not a VPN tunnel). When the packet arrives in VMc, Windows routing uses the shared OpenVPN TAP adapter that is the default gateway in VMc (set by OpenVPN when it connects) to send the packet through the VPN tunnel to the VPN provider where it enters the internet using one of their public IPs.

[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]A client configuration file that used to work looks like this (when using free vpnbook at least):
```
client
dev tun0
proto udp
remote 93.115.84.194 53
remote euro1.vpnbook.com 53      
resolv-retry infinite
nobind
persist-key
persist-tun
ca vpnbook-ca.crt
auth-user-pass         
comp-lzo
verb 3
cipher AES-128-CBC
fast-io
pull
route-delay 2
redirect-gateway

```

I have also successfully used another VPN provider that did not have a 'redirect-gateway' statement in the conf file. So it can work without one.
> redirect-gateway def1
This might be needed later though, so I will save this and try it later if it is needed (thanks!)

I don't think the problem right now is the OpenVPN configuration file, and I suspect the problem is not even in VMc. 

 I think the problem now is to get VMa to use VMc as it's default gateway. I don't know how to do that.

> VMa must have a route to VMc in order to be able to make the tunnel. But it must also use the tunnel as its default route.
Yes, and how do I do that?

When I ping 8.8.8.8 in VMa. Networking in VMa will see that this IP is not on one of the local subnets, so it tries to use the default gateway defined in VMa to reach that IP.
But when the default gateway in VMa has been set to Eth1, how can that packet route from input on Eth1 to input on VMc where it will be handled by Windows routing the same way as it used to be? I think this is the problem now.

I can not set VMc as default gateway in VMa, because VMa would not know how to get the packet from VMa to VMc when the router is in between. Next hop (i.e. default gateway) has to be Eth1.

What should routing in VMa look like to make this work? 

Maybe it's simple, but I don't understand networking well enough to figure out how to do it.





[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by The Cog on 2013-06-11
Can I step back and double-check what you are trying to achieve? 

Is the VPN tunnel between VMa (client)and VMc (server), with VMc having a normal connection to the internet via the bridged adapter?

Or is the VPN tunnel going from VMc(client) to a VPN server somewhere else on the internet, with normal routing between VMa and VMc?

I had been assuming the first of these two, but now I'm not so sure. Both seem to fit the description in your original post. They have very different answers.

---

### Post by vRouter on 2013-06-11
> Or is the VPN tunnel going from VMc(client) to a VPN server somewhere else on the internet, with normal routing between VMa and VMc?

Yes. Seems my initial explanation was less than crystal clear, sorry about that. :oops:

1. VMa runs an application which can't be trusted and which needs to use the internet. Therefore it runs in a separate VM.
2. VMc runs the OpenVPN client, which connects to an external pay-for VPN provider via a Bridged interface in VMc.
3. Normal communication between VMa and VMc.
4. When the app in VMa needs to access the internet, traffic to public IPs should be routed to VMc, which tunnels it to the VPN provider.
5. I think that basically the router should work like a patchboard, connecting VMa with VMc, and VMb with VMd. It should also let me quickly unplug a 'patch' so VMa or VMb can be isolated if the VPN tunnel in VMc or VMd goes down. I also need to firewall VMa and VMb in order to control who and what they can see.

---

### Post by The Cog on 2013-06-11
Ah, OK. I had the wrong end of the stick then.

I think that VMa and VMb both need to have the Ubuntu server eth1, 2 as their default gateway. They don't need anything more than that.

VMd can use the Ubuntu server eth3 as its default gateaway. If it needs access to the internet (I think not from your description) then you might want to configure VMc as its default gateway and add a specific route to VMb via Ubuntu eth3.

VMc needs to use the VPN tunnel as its default gateway to get to the internet, and therefore needs more specific routes to:
  VMa via Ubuntu eth3, and 
  The VPN server via the bridged adapter.
The route to VMa will probably need adding manually, but I expect that the OpenVPN client will sort out its own default route and route to the VPN server.

Similarly for VMd - default via the VPN and more specific routes for VMb and its VPN server.

I think you need to use policy routing for this, using different routing tables for VMa and VMb. I think these commands might do it, but will need trying and maybe tweaking. In case you are wondering, the table numbers were chosen arbitrarily:
```

sudo ip rule add iif eth1 table 101
sudo ip route add default via 192.168.10.3 table 101
sudo ip route add  blackhole default metric 5 table 101
sudo ip rule add iif eth2 table 102
sudo ip route add default via 192.168.10.4 table 102
sudo ip route add  blackhole default metric 5 table 102

```
The above doesn't stop VMa or VMb talking directly to the Ubuntu server or to VMc/d - if you want to block that, you need to add iptables rules. You may also need iptables rules to block VMa and VMb from talking 192.168.10.2 by IP address in case VMc and VMd helpfully forward packets back out to the other VM.

---

