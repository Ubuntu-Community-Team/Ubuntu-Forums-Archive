---
title: "Multiple NIC and multiple Gateway in Ubuntu server 12.04"
date: 2013-07-03
forum: Networking &amp; Wireless
---

### Post by hersdyanata on 2013-07-03
hi all,
first, sorry if my grammar is too bad.
i'm really really begineer working with linux.
i have some trouble with my server.

I need to config 2 multiple nic in my server.

this is my network configuration :
```

auto eth0
iface eth0 inet static
        metric 0
        address 10.1.1.112
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        gateway 10.1.1.1

auto eth1
iface eth1 inet static
        metric 1
        address 10.1.10.38
        netmask 255.255.255.252
        network 10.1.10.36
        broadcast 10.1.10.39
        gateway 10.1.10.37

```
that's all...with different class,different netmask,and different gateway.

i was try to following every step in many forums and articles but it still not works!
now i'm almost desperate because this is urgent situation and i still cant solve it.
please advice :(

---

### Post by TheFu on 2013-07-03
Well, the config files seems to be ok. I checked the 10.1.10.38 subnet - looks fine.
Are both eth0 and eth1 working?  

**ifconfig -a** sees both?

What is the routing table? **route**
Are the routers setup properly for these subnets?

Having multiple "default" routes is bad (confusing to everyone), so you might need to delete the 10.1.10.38 default route in a post-network script if that is being added automatically.  **man interfaces** explains how.

The only thing that I would change is to use metric numbers that are spread out more.  100, 200, 300, .... so there's room to do special-needs routing.

BTW, the bold items above are commands that show us what the system is actually doing vs guessing what the config file tells it.

---

### Post by hersdyanata on 2013-07-03
> **TheFu said:**
> Well, the config files seems to be ok. I checked the 10.1.10.38 subnet - looks fine.
Are both eth0 and eth1 working?  

**ifconfig -a** sees both?

What is the routing table? **route**
Are the routers setup properly for these subnets?

Having multiple "default" routes is bad (confusing to everyone), so you might need to delete the 10.1.10.38 default route in a post-network script if that is being added automatically.  **man interfaces** explains how.

The only thing that I would change is to use metric numbers that are spread out more.  100, 200, 300, .... so there's room to do special-needs routing.

BTW, the bold items above are commands that show us what the system is actually doing vs guessing what the config file tells it.

Thanks for your reply TheFu

I'm already change the metric like you said. 100 for eth0 and 200 for eth1.

This is output of [B]ifconfig -a
[/B]```

root@xxxx:/home/xxxmanager# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:5e:69:3a:1c
          inet addr:10.1.1.112  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5eff:fe69:3a1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105798 errors:0 dropped:732 overruns:0 frame:0
          TX packets:101479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13814292 (13.8 MB)  TX bytes:40879594 (40.8 MB)
          Interrupt:17 Memory:91a80000-91aa0000

eth1      Link encap:Ethernet  HWaddr 00:21:5e:69:3a:1d
          inet addr:10.1.10.38  Bcast:10.1.10.39  Mask:255.255.255.252
          inet6 addr: fe80::221:5eff:fe69:3a1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:2328 (2.3 KB)
          Interrupt:19 Memory:91980000-919a0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6847 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:584389 (584.3 KB)  TX bytes:584389 (584.3 KB)

usb0      Link encap:Ethernet  HWaddr 02:21:5e:69:3a:1f
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

I can do ping to both of them but only in the server (DMZ). i can't ping to 10.1.10.38 in my pc (client network)
this is output of **route** :
```

root@xxxx:/home/xxxmanager# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.1.1.1        0.0.0.0         UG    100    0        0 eth0
localnet        *               255.255.255.0   U     0      0        0 eth0
10.1.10.36      *               255.255.255.252 U     0      0        0 eth1

```

I don't know, but since i'm adding eth1 and everytime i config /etc/network/interfaces and then reload it. it always shows like this :
```

root@xxxx:/home/xxxmanager# /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                      RTNETLINK answers: No such process
ssh stop/waiting
ssh start/running, process 6098
RTNETLINK answers: File exists
Failed to bring up eth1.
                                                                                                     [ OK ]

```
so how to solve this Failed issue? i'm really confused @__@
because this is the first time i'm using 2 nics in linux server.
i want when i'm ping or do anything to 10.1.10.0 it's handled by eth1, not by eth0. just that.

Thanks,
Regards

---

### Post by TheFu on 2013-07-03
Well, if you look at the metric column in the routes, you can see that your settings are being ignored.
localnet is defined somewhere ... what is it?  Perhaps there is an option for route to only provide IPs?

If you are using the ssh connection, it is hard to restart it. Perhaps a server reboot is needed to see the changes? I dunno (restarting the network usually works here).

You'll only be able to ping eth1 from that subnet or from devices on the other side of that router. 

BTW, both IPs need to have different DNS and /etc/hosts names.  You probably know that, but lurkers might be confused.

Sorry, I don't have any real answers.

---

