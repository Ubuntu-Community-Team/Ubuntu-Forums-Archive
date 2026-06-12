---
title: "Problem connecting to the internet, when using 2 nics"
date: 2013-02-07
forum: Networking &amp; Wireless
---

### Post by gazza7 on 2013-02-07
Hi

I have 2 nics one connecting to a domain and one running on a private network for cloning.

(Nic1 )The one on the domain is on a 10.1.1.90 address
(Nic2) The one for cloning is on a 192.168.1.1 address

The problem is, as soon I connect the Nic 2 I loose the internet, if I uplugged the ethernet, it works fine.

The name server for Nic1  194.168.4.100 and this connected straigtout to the router via a switch.  Nic2 does to use the internet, only use for cloning on a private network, which is not connected to the damain.

---

### Post by PowerBarry43 on 2013-02-07
Hi

This sounds to me like you have a default gateway pointing to the private network. It may help if you run these commands and post the output:

```
route
cat /etc/network/interfaces
ifconfig
```

One thing to try would be running this command to add the correct gateway to your routing table.

```
route add default gw 10.1.1.1 metric 1

```
replace 10.1.1.1 with the gateway on nic1 :)

Hope this helps!

Barry

---

### Post by gazza7 on 2013-02-07
Hi

I've pasted the outputs as requested.  It looks like when the second nic is connected,  it's used for routing and pointing to clone-server102 , which is the name of the first client when I clone with Clonezill server with drbl. I'm not sure why this is happening.  the only place I can find cloneclone-server102, is in the hosts file which Clonezilla and DRBL use when cloning.  When I install Drbl and clonezilla it wipe the resolv conf file.  I have since reinstalled, but I'm still getting this problem, when the secondnic is connected. Since Drbl and clonezilla runs a script writing all the required changes to diffrent files, I'm not sure which file needs changing.

Update:It looks like whatever I put as the gateway for the second nic, it gets prefrence over the gateway on the first nic. Not sure why. The clone-server102 is being picked up from the hosts file, I put the gate way for the second nic as 192.168.1.2 and this the ip of clone-server102, when used for cloning.  Still not sure why the second nic is over riding the gateway on nic 1.

> **PowerBarry43 said:**
> Hi

This sounds to me like you have a default gateway pointing to the private network. It may help if you run these commands and post the output:

route
Output from route when botth nics connected.
```

default         clone-server102 0.0.0.0         UG    0      0        0 eth1
10.1.1.0        *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1

Output when 1 nic connected, which i use for the doamian, which i use for the internet.

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.1.1.2        0.0.0.0         UG    0      0        0 eth0
10.1.1.0        *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0

```


cat /etc/network/interfaces
output is as follows for above command.
```

auto lo
iface lo inet loopback

```

ifconfig
Output whenboth nics connecte.
```

eth0      Link encap:Ethernet  HWaddr 00:90:27:44:46:a8  
          inet addr:10.1.1.90  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:27ff:fe44:46a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:671783 errors:0 dropped:23685 overruns:0 frame:0
          TX packets:26621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:93468734 (93.4 MB)  TX bytes:3326305 (3.3 MB)

eth1      Link encap:Ethernet  HWaddr 00:21:9b:1f:55:77  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:9bff:fe1f:5577/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21073080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2576408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31537458064 (31.5 GB)  TX bytes:651601544 (651.6 MB)
          Interrupt:21 Memory:fe6e0000-fe700000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1541128 (1.5 MB)  TX bytes:1541128 (1.5 MB)


```

One thing to try would be running this command to add the correct gateway to your routing table.

```
route add default gw 10.1.1.1 metric 1

```
replace 10.1.1.1 with the gateway on nic1 :)

Tried thhe above with my gateway, but did not solve the problem.

Barry

---

### Post by TheFu on 2013-02-07
Perhaps reading the man page for interfaces will help setup the networking route metrics in the way you require?

$ **man interfaces**

Sorry I'm not a network guru, but I think if the gateways are specified with a lower metric, then that gateway gets preference over any others.  There should be a way to specify the metric in the /etc/network/interfaces file.  Yep.

---

### Post by gazza7 on 2013-02-07
Hi

To solve the problem for now i've put a getway of 0.0.0.0 on the second nic. This then lets me connect to the internet. I'm not sure if I will have to put the gateway of this computer when I need to clone. Will take a look tommorow.

Thanks to you both fot the replies.

Gazza7

---

### Post by PowerBarry43 on 2013-02-07
Hi again

> There should be a way to specify the metric in the /etc/network/interfaces file

in a server install you'd be correct but in desktop installs the interfaces file is replaced by the graphical network manager, the route tool however is present and used in both.

the problem is this entry in your routing table:

```
default         clone-server102 0.0.0.0         UG    0      0        0 eth1
```

this entry says that any outbound communications destined for networks other than 10.1.1.0 /24 or 192.168.1.0 /24 will be sent to the machine with the name clone-server102.

In short ubuntu thinks the way to the internet is clone-server102

you can try to manually remove the entry and adding the correct one by running:

```
route del default
route add default gw 10.1.1.2
```

that should get you up and running it just may reset on reboot. You should also notice that you only have and should only have one default gateway as it serves as the way out when you don't know how to get to an address. Therefore you don't need a default gateway on nic2, infact it would be undesirable as the computer would think it can get to the internet out off both interfaces.

Are you by any chance running a DHCP server on clone-server102? if you are a possible solution would be to add the default gateway address 10.1.1.2 to the DHCP config.

Hope this helps!

Barry

---

### Post by gazza7 on 2013-02-08
> **PowerBarry43 said:**
> Hi again



in a server install you'd be correct but in desktop installs the interfaces file is replaced by the graphical network manager, the route tool however is present and used in both.

the problem is this entry in your routing table:

```
default         clone-server102 0.0.0.0         UG    0      0        0 eth1
```

this entry says that any outbound communications destined for networks other than 10.1.1.0 /24 or 192.168.1.0 /24 will be sent to the machine with the name clone-server102.

In short ubuntu thinks the way to the internet is clone-server102

you can try to manually remove the entry and adding the correct one by running:

```
route del default
route add default gw 10.1.1.2
```

that should get you up and running it just may reset on reboot. You should also notice that you only have and should only have one default gateway as it serves as the way out when you don't know how to get to an address. Therefore you don't need a default gateway on nic2, infact it would be undesirable as the computer would think it can get to the internet out off both interfaces.

Are you by any chance running a DHCP server on clone-server102? if you are a possible solution would be to add the default gateway address 10.1.1.2 to the DHCP config.

Hope this helps!

Barry

After trying the following I get these results-
```
route del default

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1



```
Thn by doing
```

route add default gw 10.1.1.2



```


I get

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         clone-server002 0.0.0.0         UG    0      0        0 eth0
10.1.1.0        *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1



```


It puts the clone-server002 back as the gateway. Since the clone-server address is 192.168.1.2, I'm not sure why this is being picked up and it doesn't show the 10.1.1.2 address which is being set for the gateway.

At present I'm setting the gateway on the second nic to 0.0.0.0, which lets me out on the net, and when I use DRBL as a clone serveror or as a thin client it works, even lets me nat with the the first nic to let the thin clients access on the net.  Not to say this is the right way, but it works. Not sure if to mark this thread as solved, or does anyone else have any ideas?

---

### Post by PowerBarry43 on 2013-02-08
Hi

You may like to have a read of this:

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

The way a routing table works is it looks at the destination ip of outbound packets for example if you ping 8.8.8.8 it finds the closest match in it's routing table if you have two default gateways or default routes which are to a network 0.0.0.0 with a mask 0.0.0.0 both of these routes will match equally therefore the computer load-balance - that is to say it will send half out on one interface and half out of the other. It may be that by setting the default route to 0.0.0.0 you are effectively saying no default route which you could confirm with the output of another:
```

route
```

What concerns me is that the gateway was being automatically added in when you try to alter it. I know that for most PXE boot thin client systems DHCP is a requirement as the thins are diskless and have no initial config and also it is normal to have the server as the gateway with them nating through it but what it sounds like to me is you have one interface on the clone-server. I would consider having two interfaces on the clone-server so with that acting as a router and thins behind nating through, then set your current dual honed machine as the default gateway for the clone-server, that way you wouldn't be getting addresses from it.

Just a suggestion... that being said if you have it working you could adopt the ain't broke don't fix philosophy ;) Up to you

Hope this helps!

Barry

---

### Post by gazza7 on 2013-02-09
> **PowerBarry43 said:**
> Hi

You may like to have a read of this:

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

The way a routing table works is it looks at the destination ip of outbound packets for example if you ping 8.8.8.8 it finds the closest match in it's routing table if you have two default gateways or default routes which are to a network 0.0.0.0 with a mask 0.0.0.0 both of these routes will match equally therefore the computer load-balance - that is to say it will send half out on one interface and half out of the other. It may be that by setting the default route to 0.0.0.0 you are effectively saying no default route which you could confirm with the output of another:
```

route
```

What concerns me is that the gateway was being automatically added in when you try to alter it. I know that for most PXE boot thin client systems DHCP is a requirement as the thins are diskless and have no initial config and also it is normal to have the server as the gateway with them nating through it but what it sounds like to me is you have one interface on the clone-server. I would consider having two interfaces on the clone-server so with that acting as a router and thins behind nating through, then set your current dual honed machine as the default gateway for the clone-server, that way you wouldn't be getting addresses from it.

Just a suggestion... that being said if you have it working you could adopt the ain't broke don't fix philosophy ;) Up to you

Hope this helps!

Barry

Hi

I Already have to interfaces eth0 which is used to connect to the internet and to access my local domain. Whic uses a 10.1.1.90 address.

The other inteface eth1 is used with drbl and clonecilla to connect to the this clients. This uses a 192.168.1.1 address.
 
The problem is if both interfaces are connected I lose access to the domain and the internet on eth0, unless I set the gw to 0.0.0.0 on eth1.

I'm not sure if eth1 needs a gw, as its just connecting to thin clients with the address from 192.168.1.2 to 17  .  These are use for cloning with clonezilla.  I was also experimenting with thin client desktop which I got working and they connect to the internet by nat via 192.168.1.1 to 10.0.0.90. but will ony work if I set the gw to 0.0.0.0 on eth1.  This will then let eth0 on 10.0.0.90 connect to the internet. If I put any other address in it will not connect, I then lose connetivity with both thin clients and eth0 to the internet.

---

