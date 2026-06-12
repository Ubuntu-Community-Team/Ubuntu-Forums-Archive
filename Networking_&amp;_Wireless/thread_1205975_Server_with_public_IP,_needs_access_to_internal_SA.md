---
title: "Server with public IP, needs access to internal SAN"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by QettoE on 2009-07-06
He folks,

I have a web server with two NIC's. eth0 is connected to Internet with multiple static IP's, and eth1 to private network to connect to my storage network. Whatever I do, I can only get one of the interfaces to come up... either public or private. Here is my network script:

```
# The primary network interface
allow-hotplug eth0
iface eth0 inet static

        address 69.65.20.66
        netmask 255.255.255.248
        network 69.65.20.64
        broadcast 69.65.20.71
        gateway 69.65.20.65
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 66.28.0.61

allow-hotplug eth1
iface eth1 inet static

       address 192.168.254.66
       netmask 255.255.255.0
       network 192.168.254.0
       broadcast 192.168.254.255
       gateway 192.168.254.1

auto eth0
auto eth1

```

I understand that having two gateways might screw up networking, but I tried using one gateway with the same results.

Thanks for your attention,
Q.

---

### Post by Iowan on 2009-07-06
It would seem (to me) that you would *need* two gateways (only one would be default). What are results of **ifconfig**?

---

### Post by QettoE on 2009-07-06
> **Iowan said:**
> It would seem (to me) that you would *need* two gateways (only one would be default). What are results of **ifconfig**?

Here is my ifconfig with eth1 disabled. When I use two gw none of my adapters work for some odd reason.

```
eth0      Link encap:Ethernet  HWaddr 00:21:5a:ab:d1:98
          inet addr:69.65.20.66  Bcast:69.65.20.71  Mask:255.255.255.248
          inet6 addr: fe80::221:5aff:feab:d198/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6488147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3875181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4222200810 (3.9 GiB)  TX bytes:1183458231 (1.1 GiB)
          Interrupt:19 Memory:f8000000-f8012100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:639 (639.0 B)  TX bytes:639 (639.0 B)

```

---

### Post by Iowan on 2009-07-06
What are results of **route -n** (and **ifconfig -a**) with both interfaces enabled?

---

### Post by QettoE on 2009-07-06
> **Iowan said:**
> What are results of **route -n** (and **ifconfig -a**) with both interfaces enabled?

route -n

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
69.65.20.64     0.0.0.0         255.255.255.248 U     0      0        0 eth0
192.168.254.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.254.1   0.0.0.0         UG    0      0        0 eth1
0.0.0.0         69.65.20.65     0.0.0.0         UG    0      0        0 eth0

```

ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr 00:21:5a:ab:d1:98
          inet addr:69.65.20.66  Bcast:69.65.20.71  Mask:255.255.255.248
          inet6 addr: fe80::221:5aff:feab:d198/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:419247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:205947 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:570688473 (544.2 MiB)  TX bytes:18862731 (17.9 MiB)
          Interrupt:19 Memory:f8000000-f8012100

eth1      Link encap:Ethernet  HWaddr 00:21:5a:ab:a1:ee
          inet addr:192.168.254.66  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5aff:feab:a1ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4954 (4.8 KiB)  TX bytes:5114 (4.9 KiB)
          Interrupt:28 Memory:fa000000-fa012100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20432 (19.9 KiB)  TX bytes:20432 (19.9 KiB)

```

---

### Post by souki on 2009-07-06
hello,

you only need a private gateway if there are some servers behind this gateway

you could try this simple config (without private gateway and without allow-hotplug)
it works on several servers with different distribs

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 69.65.20.66
        netmask 255.255.255.248
        network 69.65.20.64
        broadcast 69.65.20.71
        gateway 69.65.20.65
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 66.28.0.61

auto eth1
iface eth1 inet static
       address 192.168.254.66
       netmask 255.255.255.0
       network 192.168.254.0
       broadcast 192.168.254.255
       #gateway 192.168.254.1

```

---

### Post by QettoE on 2009-07-06
Okay... I actually have to recant :)

What souki said worked fine. However, I am unable to ping the private IP given to the server, but all public IP's work. I am also unable to ping anything beyond the router from the server (private side, public sites are fine). I can ping everything connected to the switch that server is connected to, not not the rest of the VPN network (multiple offices connected through VPN).

Thanks,

---

### Post by souki on 2009-07-06
I didn't understand your previous post

you should be able to ping :
- your public adress
- your private adress
- the external gateway adress
- the internal gateway adress (enabled or not)

if the external gateway works, you should be able to ping anything outside too
if the internal gateway works (and is enabled)  you should be able to ping anything behind it

I don't know about the vpn thing, maybe you need a vpn-client to ping the internal adresses

hope it helps,
~cheers

---

### Post by QettoE on 2009-07-06
> **souki said:**
> I didn't understand your previous post

you should be able to ping :
- your public adress
- your private adress
- the external gateway adress
- the internal gateway adress (enabled or not)

if the external gateway works, you should be able to ping anything outside too
if the internal gateway works (and is enabled)  you should be able to ping anything behind it

I don't know about the vpn thing, maybe you need a vpn-client to ping the internal adresses

hope it helps,
~cheers

First off thank both of you for helping out. Much appreciated.

Here is the situation: I have a router/VPN appliance connected to this box, along with a few other servers in one location. I have a tunnel that is connecting this site to other sites. IP addresses are 192.168.254.0 for local and 192.168.1.0 and so on for remote sites. Right now I can ping anything outside the network, but can only ping servers that are connected directly to the switch. I cannot ping the linux box from other sites, and can't ping anything from the linux box that is not directly connected to the switch (remote sites).

Current situation works fine for me as I have a SAN box connected directly to the switch where my linux box is. I am just wondering why I'm unable to ping anything beyond the switch in my internal network. As if whatever gets sent to eth1 is going out from eth0 and not returning to the requester, and whatever goes out from eth1 gets lost somehow.

---

### Post by gombadi on 2009-07-06
> 
Here is the situation: I have a router/VPN appliance connected to this box, along with a few other servers in one location. I have a tunnel that is connecting this site to other sites. IP addresses are 192.168.254.0 for local and 192.168.1.0 and so on for remote sites. Right now I can ping anything outside the network, but can only ping servers that are connected directly to the switch. I cannot ping the linux box from other sites, and can't ping anything from the linux box that is not directly connected to the switch (remote sites).


From the above discussion I gather that 192.168.254.0/24 is the local network, 192.168.1.0/24 is remote via the VPN and the rest of the world exists out there via eth0.

> 
allow-hotplug eth1
iface eth1 inet static

       address 192.168.254.66
       netmask 255.255.255.0
       network 192.168.254.0
       broadcast 192.168.254.255
       gateway 192.168.254.1


From this I gather that 192.168.254.1 is the ip address of the router/VPN device.

If that is the case then you need to make sure the gateway line for eth1 is commented out because this is not a default gateway.

What you need is to add a route command for the remote network 192.168.1.0/24 so your machine will send any packets for that network to the router/VPN to be sent over the VPN.


If that is true then you need this command -
```

route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.254.1

```

---

### Post by QettoE on 2009-07-06
Thanks gombadi, and your assumptions were all correct. I'll try this tomorrow when server is not too busy and report back.

---

### Post by QettoE on 2009-07-06
If this helps, my workstations in .1 subnet can ping .254.1 gateway, but the linux box cannot ping .1.1 gateway.

---

### Post by QettoE on 2009-07-07
> **gombadi said:**
> From the above discussion I gather that 192.168.254.0/24 is the local network, 192.168.1.0/24 is remote via the VPN and the rest of the world exists out there via eth0.



From this I gather that 192.168.254.1 is the ip address of the router/VPN device.

If that is the case then you need to make sure the gateway line for eth1 is commented out because this is not a default gateway.

What you need is to add a route command for the remote network 192.168.1.0/24 so your machine will send any packets for that network to the router/VPN to be sent over the VPN.


If that is true then you need this command -
```

route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.254.1

```

Same results, but that'd do it for me since my SAN is connected directly to the switch where my Linux box is.

Thanks for all your helps folks,

---

