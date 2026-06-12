---
title: "Change Nameserver list when connection goes down?"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by KronK0321 on 2009-07-27
Hi! I've been using Ubuntu as a headless server in my basement for a couple of years. It's my samba fileserver, afp time capsule, webserver and torrent box. This forum has been a great source of information whenever I've been stuck in one way or another so thanks for that!

I recently added a second router to my network so I have 2 NICs in the Ubuntu machine: one static and one using the DHCP client. 

The Setup:

eth0 is configured with a static IP of 10.0.0.100, gateway: 10.0.0.254, netmask 255.55.255.0

eth1 is configured using DHCP. It gets a "static" IP from the DHCP server every time: 192.168.1.4, gateway 192.168.1.1, netmask 255.255.255.0. It also gets the DNS address via DHCP: 192.168.1.1


The Problem:

When both ethernet links are active, everything works great. DNS lookups are done against 192.168.1.1 and everything is speedy. When eth1 goes down (because eth0's network is connected to a UPS and eth1's is not) DNS lookups take forever. The reason is because 192.168.1.1 is still in the resolv.conf file even though there's no way to connect to it. So it tries to connect to that server before trying the other ones... for every lookup.

I've modified my dhclient.conf file to append my ISP's nameservers so that I still get name resolution when eth1 (and, subsequently, 192.168.1.1) goes down. The reason I want to keep 192.168.1.1 as the primary nameserver when eth1 is up is because it does local name resolution for the other ~10 or so clients on that network.


Possible Solutions:

[LIST]
[*]I could remove 192.168.1.1 as a nameserver and edit the hosts file on every computer connected to the 192.168.1.0/24 network. yuck.

[*]When eth0 goes down, a script could run that rewrites resolv.conf to remove 192.168.1.1 as a nameserver and then restarts /etc/init.d/networking. I'm hoping there's another, easier way though.

[*]I could suck it up and deal with slow name lookups while eth0 is down. Which is what I'm currently doing.
[/list]

Optimal Solution:

192.168.1.1 is the nameserver given to eth1 when it receives a DHCPOFFER. I'm thinking there HAS to be an automated way to clear out its information when the interface goes down. Help?


The Current Config:

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:11:2f:7b:89:35  
          inet addr:10.0.0.100  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe7b:8935/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10415 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1785187 (1.7 MB)  TX bytes:4612436 (4.3 MB)

eth1      Link encap:Ethernet  HWaddr 00:07:e9:14:58:7e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe14:587e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7263330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6837950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2153253734 (2.0 GB)  TX bytes:1287092086 (1.1 GB)
          Base address:0xdd80 Memory:fe5a0000-fe5c0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2240014 (2.1 MB)  TX bytes:2240014 (2.1 MB)

```

cat /etc/network/interfaces```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 10.0.0.100
	netmask 255.255.255.0
	network 10.0.0.0
	broadcast 10.0.0.255
	gateway 10.0.0.1
	up ifmetric eth0 50

auto eth1
iface eth1 inet dhcp
	up ifmetric eth1 1
```

cat /etc/resolv.conf
```
search lan
nameserver 192.168.1.1
nameserver 142.165.21.5
nameserver 142.165.200.5

```

cat /etc/dhcp3/dhclient.conf```

request subnet-mask, broadcast-address, time-offset, routers, domain-name, domain-name-servers, host-name, ntp-servers;
append domain-name-servers 142.165.21.5,142.165.200.5;
```

---

### Post by KronK0321 on 2009-08-01
Been a few days... bump?

---

### Post by KronK0321 on 2009-08-15
No love for DNS issues? Is there a more appropriate forum I should be posting this in/at?

---

### Post by KronK0321 on 2009-08-27
I would even love for someone -- anyone -- to point me in the right direction...

---

### Post by KronK0321 on 2009-09-23
o - kay

Thanks anyway, everyone.

---

### Post by KronK0321 on 2010-07-28
So I thought I would post the solution in case anyone else is having the same problem.

I used a couple of programs in the repository: 'resolvconf' and 'ifplugd'.

```
sudo apt-get install resolvconf ifplugd
```

The former updates the /etc/resolv.conf file when the ethernet devices go up or down.

I updated the /etc/resolvconf/interface-order file by adding the eth1 and eth0 lines:
```
# interface-order(5)
lo.inet*
lo.dnsmasq
lo.pdnsd
lo.!(pdns|pdns-recursor)
lo
tun*
tap*
[COLOR="Red"]eth1
eth0
[/COLOR]eth*
ath*
wlan*
ppp*
*

```

which writes the /etc/resolv.conf as follows when both interfaces are up:
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.1.1
nameserver 142.165.21.5
nameserver 142.165.200.5
search lan gateway.2wire.net

```

and writes it as follows when eth1 goes down with an "ifdown eth1":
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 172.16.1.254
nameserver 142.165.21.5
nameserver 142.165.200.5
search gateway.2wire.net

```

The only problem I ran into at this point was simply unplugging the ethernet cable (having the non-UPS switch go down) wasn't enough to trigger resolvconf to rewrite /etc/resolv.conf. That's where ifplugd comes in. It brings the ethernet device down when the cable is unplugged and back up when it's plugged in. 

I just had to make a change to /etc/default/ifplugd to watch the specific interfaces and to not beep:
```
INTERFACES="[COLOR="red"]eth0 eth1[/COLOR]"
HOTPLUG_INTERFACES=""
ARGS="-q -f -u0 -d10 -w -I [COLOR="red"]-b[/COLOR]"
SUSPEND_ACTION="none"

```

I hope this helps someone else! If anyone wants to chime in with a better way to do it, I'm all ears, too.

---

