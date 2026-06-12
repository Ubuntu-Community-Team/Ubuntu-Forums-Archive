---
title: "[server] setting up an ipv6 router"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by Tuna-Fish on 2011-01-27
I have a headless ubuntu server acting as a router and nat (amongst other things) for my home network. It's set up perfectly for ipv4 -- eth2 is the outgoing interface, and eth0 and eth1 form a private network, with all the other machines in the house (eth1 connects to a switch and wireless AP).

Because my isp offers ipv6 connectivity, and the recent news on how ipv4 addresses are running out, I decided to try to set up ipv6 -- also, it would be nice to have public addresses for all the other machines in the house.

I looked at a few tutorials, including [this]("https://wiki.ubuntu.com/IPv6#Configure your Ubuntu box as a IPv6 router"), but there is a problem -- the first step is to turn ipv6 forwarding on, but as it is written in /etc/sysctl.conf:
[php]
# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
[/php]
When I turn forwarding on, I lose ipv6 connectivity. I assume I should set up a static address or something, but I have no idea how. Almost all the tutorials are about ipv6 tunnels, and the rest say you should get the prefix from your isp -- and my isp doesn't seem to care about problems as long as you can reach google over ipv4. Help?

```

antuunai@toosa:~$ sudo ifconfig eth2
eth2      Link encap:Ethernet  HWaddr 00:16:01:fb:48:68  
          inet addr:130.234.182.41  Bcast:130.234.183.255  Mask:255.255.252.0
          inet6 addr: fec0::b:216:1ff:fefb:4868/64 Scope:Site
          inet6 addr: 2002:82ea:b64a:b:216:1ff:fefb:4868/64 Scope:Global
          inet6 addr: fec0::a:216:1ff:fefb:4868/64 Scope:Site
          inet6 addr: 2002:82ea:b085:a:216:1ff:fefb:4868/64 Scope:Global
          inet6 addr: fec0::8:216:1ff:fefb:4868/64 Scope:Site
          inet6 addr: 2002:82ea:b5c4:8:216:1ff:fefb:4868/64 Scope:Global
          inet6 addr: fec0::d:216:1ff:fefb:4868/64 Scope:Site
          inet6 addr: 2002:82ea:b35c:d:216:1ff:fefb:4868/64 Scope:Global
          inet6 addr: fe80::216:1ff:fefb:4868/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4005620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1056226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:733591907 (733.5 MB)  TX bytes:590901069 (590.9 MB)
          Interrupt:23 Base address:0xc00 

```
Also, it seems I get a bunch of addresses that change over time. I'd prefer a static one, and static ones for my other machines. Is that possible?

---

### Post by lemming465 on 2011-01-30
I have trouble reading the ifconfig output intelligently, and it doesn't show enough to help us decipher your problems.  Also, we need to see what is going with all of the interfaces.  Could we see the results of: ```
ip address show; ip -6 route show; ip -4 route show; ip maddr show
sudo iptable -L
sudo ip6tables -L
``` instead, please?

If your ISP has full native IPv6, your upstream modem should be sending you ICMPv6 router advertisements.  If you want your ubuntu router to provide IPv6 forwarding for the rest of your home network you will probably need to be running "radvd" on the inside interface.

The 2002:://16 addresses in your ifconfig output are 6to4 tunnel addresses, which aren't native IPv6, require a public IPv4 address, a nearby 6to4 relay, and the ability to forward packets of type IP protocol 41.  The FE80::/64 address is link-local, the IPv6 equivalent of zeroconf, and is normal.  The FEC0:: stuff is puzzling, because those are obsolete "site-local" addresses, and have been deprecated.

---

### Post by Tuna-Fish on 2011-01-30
> **lemming465 said:**
> I have trouble reading the ifconfig output intelligently, and it doesn't show enough to help us decipher your problems.  Also, we need to see what is going with all of the interfaces.  Could we see the results of: ```
ip address show; ip -6 route show; ip -4 route show; ip maddr show
sudo iptable -L
sudo ip6tables -L
``` instead, please?


```
antuunai@toosa:~$ ip address show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:04:e2:3d:ad:81 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.1/24 brd 192.168.2.255 scope global eth1
    inet6 fe80::204:e2ff:fe3d:ad81/64 scope link 
       valid_lft forever preferred_lft forever
3: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:19:66:5b:32:1f brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.1/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::219:66ff:fe5b:321f/64 scope link 
       valid_lft forever preferred_lft forever
4: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:16:01:fb:48:68 brd ff:ff:ff:ff:ff:ff
    inet 130.234.182.41/22 brd 130.234.183.255 scope global eth2
    inet6 2002:82ea:b085:a:216:1ff:fefb:4868/64 scope global dynamic 
       valid_lft 7039sec preferred_lft 1639sec
    inet6 fec0::a:216:1ff:fefb:4868/64 scope site dynamic 
       valid_lft 7039sec preferred_lft 1639sec
    inet6 fe80::216:1ff:fefb:4868/64 scope link 
       valid_lft forever preferred_lft forever


antuunai@toosa:~$ ip -6 route show;
2002:82ea:b085:a::/64 dev eth2  proto kernel  metric 256  expires 7029sec mtu 1500 advmss 1440 hoplimit 4294967295
fe80::/64 dev eth1  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 4294967295
fe80::/64 dev eth0  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 4294967295
fe80::/64 dev eth2  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 4294967295
fec0:0:0:a::/64 dev eth2  proto kernel  metric 256  expires 7029sec mtu 1500 advmss 1440 hoplimit 4294967295
default via fe80::f0a1:fa2a:aa44:d536 dev eth2  proto kernel  metric 1024  expires 55220sec mtu 1500 advmss 1440 hoplimit 4294967295
default via fe80::ed56:7d61:9190:3ebf dev eth2  proto kernel  metric 1024  expires 47329sec mtu 1500 advmss 1440 hoplimit 4294967295
default via fe80::c5e4:56b8:b00e:a61b dev eth2  proto kernel  metric 1024  expires 54026sec mtu 1500 advmss 1440 hoplimit 4294967295
default via fe80::700a:e929:8f1f:cac6 dev eth2  proto kernel  metric 1024  expires 54441sec mtu 1500 advmss 1440 hoplimit 4294967295
default via fe80::9146:690e:b004:1f24 dev eth2  proto kernel  metric 1024  expires 65364sec mtu 1500 advmss 1440 hoplimit 4294967295


antuunai@toosa:~$ ip -4 route show;
192.168.2.0/24 dev eth1  proto kernel  scope link  src 192.168.2.1 
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.1 
130.234.180.0/22 dev eth2  proto kernel  scope link  src 130.234.182.41 
default via 130.234.180.1 dev eth2  metric 100 


antuunai@toosa:~$ ip maddr show
1:	lo
	inet  224.0.0.1
	inet6 ff02::1
2:	eth1
	link  33:33:00:00:00:01
	link  01:00:5e:00:00:01
	link  33:33:ff:3d:ad:81
	link  33:33:00:00:00:fb
	link  01:00:5e:00:00:fb
	inet  224.0.0.251
	inet  224.0.0.1
	inet6 ff02::fb
	inet6 ff02::1:ff3d:ad81
	inet6 ff02::1
3:	eth0
	link  33:33:00:00:00:01
	link  01:00:5e:00:00:01
	link  33:33:ff:5b:32:1f
	link  33:33:00:00:00:fb
	link  01:00:5e:00:00:fb
	inet  224.0.0.251
	inet  224.0.0.1
	inet6 ff02::fb
	inet6 ff02::1:ff5b:321f
	inet6 ff02::1
4:	eth2
	link  33:33:00:00:00:01
	link  01:00:5e:00:00:01
	link  33:33:ff:fb:48:68
	link  33:33:00:00:00:fb
	link  01:00:5e:00:00:fb
	inet  224.0.0.251
	inet  224.0.0.1
	inet6 ff02::fb
	inet6 ff02::1:fffb:4868 users 3
	inet6 ff02::1


antuunai@toosa:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere            tcp spt:webmin 
DROP       udp  --  anywhere             anywhere            udp dpts:netbios-ns:netbios-dgm 
DROP       tcp  --  anywhere             anywhere            tcp multiport dports loc-srv,netbios-ssn,microsoft-ds 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination       


antuunai@toosa:~$ sudo ip6tables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    
```

> 
If your ISP has full native IPv6, your upstream modem should be sending you ICMPv6 router advertisements.  If you want your ubuntu router to provide IPv6 forwarding for the rest of your home network you will probably need to be running "radvd" on the inside interface.

I'm probably being stupid here, but when I enable forwarding, how can I still get a public address on the outgoing interface? I'm not even getting anywhere near running radvd yet -- the second I turn the ipv6 forwarding knob on, I no longer have ipv6.

> The 2002:://16 addresses in your ifconfig output are 6to4 tunnel addresses, which aren't native IPv6, require a public IPv4 address, a nearby 6to4 relay, and the ability to forward packets of type IP protocol 41.

The tunnel was certainly not set up by me. Does this mean that my ISP's idea of ipv6 is running a tunnel that sends routing advertisements for all it's customers? If yes, is it even theoretically possible to connect multiple machines from the same subnet (and only one public ipv4 address) onto it?

> The FE80::/64 address is link-local, the IPv6 equivalent of zeroconf, and is normal.  The FEC0:: stuff is puzzling, because those are obsolete "site-local" addresses, and have been deprecated.

I've been trying to contact people who know anything about ipv6 at my ISP, and I'm starting to think it was all set up years ago and not touched since. Deprecated addresses reinforce this belief.

And this is one in the fraction of a percent that advertises ipv6 connectivity.

---

### Post by lemming465 on 2011-02-01
> **Tuna-Fish said:**
> ... when I enable forwarding, how can I still get a public address on the outgoing interface?
I think with forwarding on the kernel expects you to statically configure routes and interfaces.  On the one Linux box I've got with native v6, setting forwarding seems at least to remove the default routes.  As an experiment, with forwarding off run "ip -6 addr show; ip -6 route show",
turn on forwarding, wait about 4 minutes to let it react to router advertisements in the new regime, then run the "ip" commands again and see what changed.


> .. is it even theoretically possible to connect multiple machines from the same subnet (and only one public ipv4 address)
On the IPv4 side, with only one address on the outside interface (eth2), you need NAT44 for multiple inside hosts.  On the IPv6 side, the outside has a /64 subnet, which can support a completely insane number of hosts.  Typically I think would just advertise the exact same subnet from radvd, but using your link-local (FE80::...) address of the inside interface as the gateway address, instead of the ISP's gateway address.  Which is where the IP forwarding comes into play.

> I've been trying to contact people who know anything about ipv6 at my ISP, and I'm starting to think it was all set up years ago and not touched since. Deprecated addresses reinforce this belief.

And this is one in the fraction of a percent that advertises ipv6 connectivity.
The next few years are going to be a bit exciting, and we lucky few get to be on the bleeding edge.  By 2015 I expect most of the planet will have decent IPv6 available; but early adopters are in for some R&D and brokenness.

---

