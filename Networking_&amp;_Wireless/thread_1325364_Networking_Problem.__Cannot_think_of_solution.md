---
title: "Networking Problem.  Cannot think of solution"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by gmalenko on 2009-11-13
Hey guys
My ubuntu box will be acting as my main router/fileserver etc for home use.  
However,  I am unable to let it run live because of an issue I am having.  No matter what I do, the machine doesnt get to the internet nor does it allow clients behind it get to the net.  Now I've taken the firewall offline and no help.  I am running out of ideas how to get it to work.  This machine will be replacing an out of date Fedora machine but since its not acting right, it still doesnt work.

Any help?  What information do you need from me?

---

### Post by Iowan on 2009-11-13
Is the box using Network Manager (or is it a server install)?  Post contents of */etc/network/interfaces* (won't be too useful on a NM-managed box). Post results of **ifconfig -a**. If the interface (eth0?) has no IP address, also post results of **lshw -C network**.

---

### Post by gmalenko on 2009-11-13
I'll post it in a few minutes.  But the computer is a server install.

---

### Post by gmalenko on 2009-11-13
Here is some info about the machine

The computer has 2 nics in it.  1 (eth0)for the outside (comcast) the other internal for the lan (eth1).
When hooked up directory (as it should be) to comcast, eth0 does indeed get an ipaddress.  DHCPD is configigured to run off of eth1 and the machine does assign ipaddress to the internal lan.  
I have used fwbuilder to create a firewall.  Masqurade is on and good to go.  The configuration is a clone from my old fedora machine.  Its not directly ported, but remade...if that makes any sense at all.  
Now, when the box is hooked directly to comcast, no machine (including the box) can access the internet.  First I check to see if it was getting a valid ipaddress from comcast.  Next step was to disable the firewall (iptables) to see if the problem lies there.  When I disabled the firewall, I still get no type of internet connection.  

What are the commands that will help me diagnose what is going wrong with the machine?  Netstat -r looks good.  I will post it tonight when I hook the machine back to comcast to test.  

In the mean time, any recommendations on what to run and what to post?

---

### Post by gmalenko on 2009-11-13
*/etc/network/interfaces*
```

#loopback
auto lo
iface lo inet loopback

#internet
auto eth0
iface eth0 inet dhcp

#internal
auto eth1
iface eth1 inet static
address 192.168.10.1
netmask 255.255.255.0
network 192.168.10.0
broadcast 192.168.10.255
pre-up iptables-restore < /etc/iptables.rules



```

---

### Post by Iowan on 2009-11-13
I don't see a gateway definition - does a default gateway show up in **route**?

---

### Post by gmalenko on 2009-11-13
Thank you for your help so far.

I figured out what the problem was.  It was with my iptables configuration.  I was staring at it and it hit me what the issue was.  

But I did forget to put gateway in that.  Thank you for pointing it out to me.

---

### Post by VcDeveloper on 2012-03-01
Hi, I need help getting started in the same direction.  Simple home network, 1 server, 1 work station

Comcast : Motorola SB5100 Cable Modem
|
Dynex Router: 4 ports, using only 1, want to control Internet access using Ubuntu
|
Ubuntu 11.04 : 2 NIC's

[LIST]
[*]    eth0 : Comcast
[*]    eth1: Work Station: dual boot | openSuSe 12.1, Windows 7
[/LIST]

So far I can't get the work station to access the Internet, new at this phase of configuration, doing a lot of reading, but need help at the same time.  Not sure if this is the best structure to use.  Here's the output of what I have:

**interfaces:**
```
auto lo
iface lo inet loopback
```**netstat:**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0
```**lshw:**
```

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:19:db:cc:66:00
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.102 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:d800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff
  *-network
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 11
       serial: 00:12:17:56:cf:1e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=64 maxlatency=128 mingnt=64 multicast=yes
       resources: irq:16 ioport:e800(size=256) memory:febffc00-febfffff memory:febc0000-febdffff
```**ifconfig:**
```
eth0      Link encap:Ethernet  HWaddr 00:19:db:cc:66:00  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fecc:6600/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:331357 (331.3 KB)  TX bytes:70451 (70.4 KB)
          Interrupt:44 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:12:17:56:cf:1e  
          inet6 addr: fe80::212:17ff:fe56:cf1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1440 (1.4 KB)  TX bytes:2394 (2.3 KB)
          Interrupt:16 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```I tried to direct connect to the Modem Cable, but couldn't get an IP address,  so I put it back like above.  I currently have ufw enable with its default.   However I did make some changes to:

**/etc/default/ufw**
```

# Set the default forward policy to ACCEPT, DROP or REJECT.  Please note that
# if you change this you will most likely want to adjust your rules
DEFAULT_FORWARD_POLICY="ACCEPT"

```**/etc/ufw/sysclt.conf**
```

# Uncomment this to allow this host to route packets between interfaces
net/ipv4/ip_forward=1
net/ipv6/conf/default/forwarding=1

```**/etc/sysclt.conf**
```

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
net.ipv6.conf.all.forwarding=1

```**I did have this, but removed for now /etc/before.rules:**
```

# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT

```I would like to have the server direct connect so I can use the router for the LAN, but, what's could be keeping Ubuntu from establishing an IP.

---

