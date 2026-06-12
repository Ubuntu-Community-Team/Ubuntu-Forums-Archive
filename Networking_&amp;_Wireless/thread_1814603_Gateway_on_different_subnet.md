---
title: "Gateway on different subnet"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by hewbert on 2011-07-29
Greetings,

I'm trying to setup routes for a gateway that resides on a different subnet.

Our ISP leased us a block of IPs and told us to route through the current gateway, which is on a different subnet than our current block of addresses.

To test, I've enabled one of the new addresses on one of the existing machines, which works.  That machine has an address on the same subnet as the gateway, however.

The gateway address is 24.111.1.177
One of the new addresses I'm trying to use is 96.2.192.130, netmask= 255.255.255.240, broadcast= 96.2.192.143

Obviously, I can't just specify that gateway in /etc/network/interfaces without some routing, which is where the trouble I'm having is.  The machine I'm trying to set this up on is part of 2 networks - one internal, on two different NICs.

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 52:54:00:5c:f8:ed  
          inet addr:172.30.112.122  Bcast:172.30.112.255  Mask:255.255.240.0
          inet6 addr: fe80::5054:ff:fe5c:f8ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5455581 (5.4 MB)  TX bytes:2206061 (2.2 MB)

eth1      Link encap:Ethernet  HWaddr 52:54:00:31:8c:ac  
          inet addr:96.2.192.130  Bcast:96.2.192.143  Mask:255.255.255.240
          inet6 addr: fe80::5054:ff:fe31:8cac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:17220 (17.2 KB)
```

I've been tinkering with the routing, but haven't been able to get it.

I need the 96.2.192.130 address to have a gateway of 24.111.1.177 and the 172.30.112.122 to have a gateway of 172.30.112.1

Any ideas here?

[http://ubuntuforums.org/showthread.php?t=1510986]("http://ubuntuforums.org/showthread.php?t=1510986") is a similar thread, but the solution there didn't seem to work in my case.

---

### Post by bab1 on 2011-07-29
> **hewbert said:**
> Greetings,

I'm trying to setup routes for a gateway that resides on a different subnet.

Our ISP leased us a block of IPs and told us to route through the current gateway, which is on a different subnet than our current block of addresses.

To test, I've enabled one of the new addresses on one of the existing machines, which works.  That machine has an address on the same subnet as the gateway, however.

The gateway address is 24.111.1.177
One of the new addresses I'm trying to use is 96.2.192.130, netmask= 255.255.255.240, broadcast= 96.2.192.143

Obviously, I can't just specify that gateway in /etc/network/interfaces without some routing, which is where the trouble I'm having is.  The machine I'm trying to set this up on is part of 2 networks - one internal, on two different NICs.

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 52:54:00:5c:f8:ed  
          inet addr:172.30.112.122  Bcast:172.30.112.255  Mask:255.255.240.0
          inet6 addr: fe80::5054:ff:fe5c:f8ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5455581 (5.4 MB)  TX bytes:2206061 (2.2 MB)

eth1      Link encap:Ethernet  HWaddr 52:54:00:31:8c:ac  
          inet addr:96.2.192.130  Bcast:96.2.192.143  Mask:255.255.255.240
          inet6 addr: fe80::5054:ff:fe31:8cac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:17220 (17.2 KB)
```

I've been tinkering with the routing, but haven't been able to get it.

I need the 96.2.192.130 address to have a gateway of 24.111.1.177 and the 172.30.112.122 to have a gateway of 172.30.112.1

Any ideas here?

[http://ubuntuforums.org/showthread.php?t=1510986]("http://ubuntuforums.org/showthread.php?t=1510986") is a similar thread, but the solution there didn't seem to work in my case.

What didn't work?  What error codes did you see?  What do the routing tables look like?  Post the output of ```
route -n
```

---

### Post by hewbert on 2011-07-29
> **bab1 said:**
> What didn't work?  What error codes did you see?  What do the routing tables look like?  Post the output of ```
route -n
```

I apologize, I should've been more verbose.  I just wasn't sure where to begin - the routing was subject to a lot of experimentation.

I haven't seen any error codes outside of my improper syntax with 'route' and 'ip route'. 

Here's what I have in /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address     172.30.112.122
    network     172.30.112.0
    netmask     255.255.240.0
    broadcast   172.30.112.255
   gateway     172.30.112.1
    dns-nameservers 172.30.112.121
    dns-search  dsdk12.schoollocal


auto eth1
iface eth1 inet static
    address 96.2.192.130
    netmask 255.255.255.240
    broadcast 96.2.192.143  <- That's what the ISP gave me, but I'm not sure it's used if I'm on a different subnet
#    gateway 24.111.1.177
 
```

I've tried a pretty barebones configuration for eth1 - leaving out the broadcast.

I've tried combinations of setting no gateways for either interface, too, and setting them with 'route'

With that config, after a fresh boot, route -n provides:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
96.2.192.128    0.0.0.0         255.255.255.248 U     0      0        0 eth1
172.30.112.0    0.0.0.0         255.255.240.0   U     0      0        0 eth0

```

Then I tried this:
```

root@ns2:~# route add -host 24.111.1.177 dev eth1
root@ns2:~# route add default dev eth1 gw 24.111.1.177
root@ns2:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
24.111.1.177    0.0.0.0         255.255.255.255 UH    0      0        0 eth1
96.2.192.128    0.0.0.0         255.255.255.248 U     0      0        0 eth1
172.30.112.0    0.0.0.0         255.255.240.0   U     0      0        0 eth0
0.0.0.0         24.111.1.177    0.0.0.0         UG    0      0        0 eth1

```

And still can't reach it. 

Thanks for the response!

---

### Post by bab1 on 2011-07-30
> **hewbert said:**
> To test, I've enabled one of the new addresses on one of the existing machines, which works. That machine has an address on the same subnet as the gateway, however.

The gateway address is 24.111.1.177
One of the new addresses I'm trying to use is 96.2.192.130, netmask= 255.255.255.240, broadcast= 96.2.192.143

I have to assume what you mean here is that the block of addresses consists of```

96.2.192.128/28 = Network (subnet)
96.2.192.128 = Network ID
96.2.192.129 = 1st usable host address
96.2.192.142 = last usable host address
96.2.192.143 = broadcast address for this subnet

24.111.1.177 = gateway device

```

Your interfaces file has some odd entries (see my remarks in **[COLOR="Red"]bold red[/COLOR]**).
> 
Here's what I have in /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address     172.30.112.122
    network     172.30.112.0
    netmask     255.255.240.0  **[COLOR="Red"]<-This network has 4096 hosts[/COLOR]**
    broadcast   172.30.112.255 **[COLOR="Red"]<-s/b 172.30.127.255 with above netmask[/COLOR]**
   gateway     172.30.112.1
    dns-nameservers 172.30.112.121 **[COLOR="Red"]< - Did you manually add these?[/COLOR]**
    dns-search  dsdk12.schoollocal


auto eth1
iface eth1 inet static
    address 96.2.192.130
    netmask 255.255.255.240
    broadcast 96.2.192.143  <- That's what the ISP gave me, but I'm not sure it's used if I'm on a different subnet **[COLOR="Red"]<- You are not on a separate subnet -- the gateway device is[/COLOR]**
#    gateway 24.111.1.177 [COLOR="Red"]<- this needs to be declared in a script or with upstart[/COLOR]
 
```



I've tried a pretty barebones configuration for eth1 - leaving out the broadcast.

I've tried combinations of setting no gateways for either interface, too, and setting them with 'route'

With that config, after a fresh boot, route -n provides:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
96.2.192.128    0.0.0.0         255.255.255.248 U     0      0        0 eth1
172.30.112.0    0.0.0.0         255.255.240.0   U     0      0        0 eth0

```
No Gateway listed in the above output.  Under Flags we have a U for up interface only.> 
Then I tried this:
```

root@ns2:~# route add -host 24.111.1.177 dev eth1
root@ns2:~# route add default dev eth1 gw 24.111.1.177
root@ns2:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
24.111.1.177    0.0.0.0         255.255.255.255 UH    0      0        0 eth1
96.2.192.128    0.0.0.0         255.255.255.248 U     0      0        0 eth1
172.30.112.0    0.0.0.0         255.255.240.0   U     0      0        0 eth0
0.0.0.0         24.111.1.177    0.0.0.0         UG    0      0        0 eth1

```

How does the 172.30.112.0 network get tot the Internet. Are you using this host as a router?  Do you forward eth0 to eth1?

---

### Post by hewbert on 2011-07-30
> **bab1 said:**
> I have to assume what you mean here is that the block of addresses consists of```

96.2.192.128/28 = Network (subnet)
96.2.192.128 = Network ID
96.2.192.129 = 1st usable host address
96.2.192.142 = last usable host address
96.2.192.143 = broadcast address for this subnet

24.111.1.177 = gateway device

```


Yes, that's right.

> 
Your interfaces file has some odd entries (see my remarks in **[COLOR="Red"]bold red[/COLOR]**).
auto eth0
iface eth0 inet static
    address     172.30.112.122
    network     172.30.112.0
    netmask     255.255.240.0  <-This network has 4096 hosts
    broadcast   172.30.112.255 <-s/b 172.30.127.255 with above netmask
   gateway     172.30.112.1
    dns-nameservers 172.30.112.121 < - Did you manually add these?
    dns-search  dsdk12.schoollocal


auto eth1
iface eth1 inet static
    address 96.2.192.130
    netmask 255.255.255.240
    broadcast 96.2.192.143  <- That's what the ISP gave me, but I'm not sure it's used if I'm on a different subnet <- You are not on a separate subnet -- the gateway device is
#    gateway 24.111.1.177 <- this needs to be declared in a script or with upstart


Yes, 4096 hosts. I'll adjust that broadcast, thanks.  Yes, I added those dns settings.  I realize they're pointless with resolv.conf.

I know I'm not on a different subnet than the .143 broadcast - I was referring to "different subnet than the gateway."
I commented out the gateway there while messing with all of this.  Uncommenting it results in error, since it's on a different subnet (SIOCADDRT: No such process)

> 
No Gateway listed in the above output.  Under Flags we have a U for up interface only.
How does the 172.30.112.0 network get tot the Internet. Are you using this host as a router?  Do you forward eth0 to eth1?

No, it's not a router.  I didn't set that route myself, this is what was in the routing tables after a fresh boot (without specifying a gateway in /etc/network/interfaces).  It *doesn't* get out right now that I've been working on making the other adapter work (I know how to make it, though).

---

### Post by bab1 on 2011-07-31
> **hewbert said:**
> 
I know I'm not on a different subnet than the .143 broadcast - I was referring to "different subnet than the gateway."

I'm a little confused here.  In an earlier post you stated *[COLOR="DarkGreen"]"To test, I've enabled one of the new addresses on one of the existing machines, which works. That machine has an address on the same subnet as the gateway, however."[/COLOR]*

To me that means the host 24.111.1.177 is a gateway host (most probably a router).  Yet you say this is not so (see below).
> 

No, it's not a router.  I didn't set that route myself, this is what was in the routing tables after a fresh boot (without specifying a gateway in /etc/network/interfaces).  It *doesn't* get out right now that I've been working on making the other adapter work (I know how to make it, though).

Who is setting the gateway?  The routing table is a reflection of the setup on your host.  You should be in control.  If you are using DHCP to set the gateway then it must hand out the correct configuration.  

If I was playing with this I would down the eth0 interface and manually set up only eth1 interface.  Having a multi-homed device just adds to the confusion in this case.  The best way to check anything is to remove as many variables from the equation as you can.  Consider this: From the terminal can you say with any certainty that a ping goes out eth1 (instead of eth0)?  Why do you need to have 2 interfaces in the host you are using?   

Once you are dealing with a host with only 1 interface you can configure it with *route add* and then declaring that route as the route to the GW.  This method does work as long as the gateway you are attempting to use will accept connection from your subnet.  If the subnet you are using is not recognized by the gateway it will not work.  I'm sure, that at the very least, it refuses to pass packets with an origin using private network addressing (Nat addresses).

---

### Post by hewbert on 2011-07-31
> **bab1 said:**
> I'm a little confused here.  In an earlier post you stated *[COLOR="DarkGreen"]"To test, I've enabled one of the new addresses on one of the existing machines, which works. That machine has an address on the same subnet as the gateway, however."[/COLOR]*

To me that means the host 24.111.1.177 is a gateway host (most probably a router).  Yet you say this is not so (see below).


I have a machine that has a 24.111.1.x address and uses the .177 for a gateway.  I just made an interface alias to test the 96.2.192.30 address on that machine.  That's what I mean.  24.111.1.177 is definitely the gateway.  I apologize if my poor explanation wasn't clear, but it's certainly the gateway.

> 
Who is setting the gateway?  The routing table is a reflection of the setup on your host.  You should be in control.  If you are using DHCP to set the gateway then it must hand out the correct configuration.  


The network configuration in the above post is all I've done.  The things shown above are all I've set.  There's no DHCP involved here.

> 
If I was playing with this I would down the eth0 interface and manually set up only eth1 interface.  Having a multi-homed device just adds to the confusion in this case.  The best way to check anything is to remove as many variables from the equation as you can.  Consider this: From the terminal can you say with any certainty that a ping goes out eth1 (instead of eth0)?  Why do you need to have 2 interfaces in the host you are using?   

Once you are dealing with a host with only 1 interface you can configure it with *route add* and then declaring that route as the route to the GW.  This method does work as long as the gateway you are attempting to use will accept connection from your subnet.  If the subnet you are using is not recognized by the gateway it will not work.  I'm sure, that at the very least, it refuses to pass packets with an origin using private network addressing (Nat addresses).

This machine has 2 NICs to provide internal DNS services and 'external' DNS services.  I know that two interfaces aren't necessary, but it's preferable to me in this case.

I can try eliminating one of the interfaces.  In the meantime, I've asked the ISP if I could just get a gateway on the same subnet.  This just seems silly to me.

---

### Post by bab1 on 2011-07-31
> **hewbert said:**
> I have a machine that has a 24.111.1.x address and uses the .177 for a gateway.  
This means that the .177 host is a gateway host.  This is a specifically configured host (a physical device).  It forwards packets out of one network into another.> 
I just made an interface alias to test the 96.2.192.30 address on that machine.  That's what I mean. 
Huh???? This makes no networking sense.> 
 24.111.1.177 is definitely the gateway.  I apologize if my poor explanation wasn't clear, but it's certainly the gateway.
As we have said before.> 
The network configuration in the above post is all I've done.  The things shown above are all I've set.  There's no DHCP involved here.

This machine has 2 NICs to provide internal DNS services and 'external' DNS services.  I know that two interfaces aren't necessary, but it's preferable to me in this case.
Are you making zone transfers from one side to another directly on this machine (internally on this host)?> 

I can try eliminating one of the interfaces.  In the meantime, I've asked the ISP if I could just get a gateway on the same subnet.  This just seems silly to me.

It's not silly at all.  When you subnet blocks of a network this is how it is handled.  It's not seen often in home installations due to NAT being used.  I believe the ISP  can provide a working gateway.  I believe you should talk to them.  It is possible that the gateway is rejecting the addresses in the 96.2.192.128/28 range.  This is something the ISP should be able to workout for you.

On the other hand you may have configuration problems on you machine.

---

### Post by hewbert on 2011-07-31
> **bab1 said:**
> This means that the .177 host is a gateway host.  This is a specifically configured host (a physical device).  It forwards packets out of one network into another.

Yes... I was clearing up your question of "are you saying it's not a router."

> 
Huh???? This makes no networking sense.As we have said before.

Why not?  I created eth1:1 and gave it that address.

> 
Are you making zone transfers from one side to another directly on this machine (internally on this host)?


If I understand you right - no.  It is a secondary DNS server for internal hosts and public-facing hosts.

> 
It's not silly at all.  When you subnet blocks of a network this is how it is handled.  It's not seen often in home installations due to NAT being used.  I believe the ISP  can provide a working gateway.  I believe you should talk to them.  It is possible that the gateway is rejecting the addresses in the 96.2.192.128/28 range.  This is something the ISP should be able to workout for you.  On the other hand you may have configuration problems on you machine.

I've looked all over for material on this and have tried many of the suggestions, but yielded no success.  It's definitely possible that it's an issue on my end, but given that I've followed a number of instructions from other folks that have done something similar, I'm suspicious that the gateway is just rejecting the new subnet.  By silly, I mean going through all the trouble when I could likely get a gateway on the same subnet.

I don't know what we've gained from this thread other than confusion.

---

