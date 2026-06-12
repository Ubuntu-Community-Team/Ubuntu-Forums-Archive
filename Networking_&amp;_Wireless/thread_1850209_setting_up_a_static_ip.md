---
title: "setting up a static ip"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by manish411 on 2011-09-26
I have a lan connection in my cllg. hostel in which every room has a lan port.
I want to have my port a static ip.
Initially my ip is 192.168.24.137

I have editied the interfaces file as

```

 auto eth0
iface lo inet static
address 192.168.24.12
netmask 255.255.255.0
network 192.168.24.0
broadcast 192.168.24.255
gateway 192.168.24.1


```
after running 

```


$sudo ifdown eth0 
$Ignoring unknown interface eht0=eht0.
$sudo ifup eth0
$Ignoring unknown interfaces eth0 = eth0


```

I want my laptop to have a static ip as 192.168.24.12
What is the static ip if I am requesting is already in use??

---

### Post by Porcini M. on 2011-09-26
Your interfaces file should look something like this:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.110
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.254

```

Type "ifconfig" to see what interfaces are available.

---

### Post by manish411 on 2011-09-26
> Type "ifconfig" to see what interfaces are available.

```

utkarsh@utkarsh-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:54:4f:5e  
          inet addr:192.168.24.137  Bcast:192.168.24.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe54:4f5e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:203919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:123143 errors:0 dropped:0 overruns:0 carrier:13
          collisions:0 txqueuelen:1000 
          RX bytes:222615516 (222.6 MB)  TX bytes:15763018 (15.7 MB)
          Interrupt:45 

```

---

### Post by papibe on 2011-09-26
Are you using the Desktop version of Ubuntu or the server? I ask you this because the way to do this varies between those versions.

Regards.

BTW, if you do not admin the network, setting your PC to a static IP is not a good idea. For example if other PC has already the address 192.168.24.12, your connection will either don't work, be very slow, or produce problems to the other user.

If for some important reason you 'need' that specific address, the way to make it work is to talk with the network manager.

---

### Post by manish411 on 2011-09-26
I am using the Desktop version of Ubuntu 10.10
 
I am doing this because I am learning to do network administration 
in Linux!!

---

### Post by papibe on 2011-09-26
Restore your /etc/network/interfaces to what it was:
```
auto lo
iface lo inet loopback

```
Then open 'Network Connections'. Select eth0 and press edit. Go to the IPv4 tab and select 'Manual' as a Method. Add and address and edit the necesary fields. Probably you are going to use the same DNS provided by your network.

That's it.

Again a bit of warning: Don't actually do this without coordination with your network administration manager. If that address is a well know machine on the network, like a server, you can get in serious troubles for trying to supplant its IP (even inadvertently).

Regards.

---

