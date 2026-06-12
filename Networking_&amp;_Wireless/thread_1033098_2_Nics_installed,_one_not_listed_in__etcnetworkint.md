---
title: "2 Nics installed, one not listed in  /etc/network/interfaces and does not function."
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by digitldrug on 2009-01-07
Hi All,

I have 2 NICs installed, but one is not listed in  /etc/network/interfaces and does not function.

There is a lot floating around in my head right now so I'll try to keep this as organized as possible. Please keep in mind,I know little to nothing about linux (2 weeks in).  I have, however, read enough posts/articles to make my head swim so any commands or knowledge I display is an illusion.  
ie:  Be gentle, its my first time. 

System:
Ubuntu Server 8.10 fresh install (also installed Xfce)
Everex gPc2 Via C7 1.5ghz 1GB Ram
2 NICS
	realtek onboard  (Eth0) Works!
	Netgear GA630 Gigabit Ethernet rev 01 (No Eth alias assigned/not listed in interfaces file)

Steps to Resolve:
Step 1
Ran lspci -v to ensure that nic is detected and driver is loaded for netgear.

output:
00:09.0 Ethernet controller: Netgear GA630 Gigabit Ethernet (rev 01)
	Subsystem: Netgear GA630 Gigabit Ethernet
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at f6000000 (32-bit, non-prefetchable) [size=16K]
	Kernel driver in use: acenic
	Kernel modules: acenic

I googled acenic and this appears to be the correct driver.

Step 2
Assigned eth0 a static IP, rebooted. and added an eth1 entry manually.  The resulting file is pasted below:

#The following line causes the listed adapters to be enabled during startup
auto lo eth0 eth1


# The loopback network interface
iface lo inet loopback

# The primary network interface 10/100 onboard
iface eth0 inet static
        address 192.168.0.3
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1

# PCI NetGear GA630 10/100/1000
 iface eth1 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1

This obviously didn't work, and I'm not clear on where the eth0/eth1 aliases would be assigned to a specific hardware device.  I tried etc/modprob.d/aliases but did not find any Eth* entries, including one for eth0.

Additional Info:
I tried pinging via specific adapters 
The results are below.  eth0 was successful, but what I found interesting was that eth1 reported the same IP as eth0.

digitldrug@viaserver:~$ ping google.com -I eth0
PING google.com (72.14.205.100) from 192.168.0.3 eth0: 56(84) bytes of data.
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=1 ttl=247 time=833 ms
64 bytes from qb-in-f100.google.com (72.14.205.100): icmp_seq=2 ttl=247 time=864 ms
...


digitldrug@viaserver:~$ ping google.com -I eth1
PING google.com (74.125.45.100) from 192.168.0.3 eth1: 56(84) bytes of data.
From viaserver.local (192.168.0.3) icmp_seq=2 Destination Host Unreachable
From viaserver.local (192.168.0.3) icmp_seq=3 Destination Host Unreachable
...


I hope I've provided enough information and if you have any questions or I left something important out, don't hesitate to ask.  Thank you in advance.

- Jordan

---

### Post by digitldrug on 2009-01-07
Oh sorry, forgot - here is my ifconfig output

digitldrug@viaserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:52:fe:41  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe52:fe41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:290325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:402271974 (402.2 MB)  TX bytes:11446098 (11.4 MB)
          Interrupt:18 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:02:e3:00:4e:ba  
          inet6 addr: fe80::202:e3ff:fe00:4eba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3710 (3.7 KB)  TX bytes:20507 (20.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:394 errors:0 dropped:0 overruns:0 frame:0
          TX packets:394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34672 (34.6 KB)  TX bytes:34672 (34.6 KB)

---

### Post by Yashiro on 2009-01-07
And what are you trying to achieve using these two cards?

---

### Post by digitldrug on 2009-01-07
Ultimately I would just like to have the box connected via gigabit, and I am not really concerned with the onboard realtek (10/100).  I am simply using the onboard right now to diagnose my problem.

Unfortunately I am having trouble with the gigabit card, as I've described in my original post.

In the distant future maybe I would experiment with gateway/routing/etc via the onboard nic, but that would be in the distant future and is not my primary concern.

- Jordan

PS: Yes my router/switch is gigabit already, and my desktop will be receiving the gigabit treatment next (new convert from vista to Ubuntu).

---

### Post by Iowan on 2009-01-07
It may not work well having both cards in the same subnet (192.168.0.X). (Plays havoc with routing) Try putting eth1 elsewhere (like 192.168.1.3).  
Another suggestion from another thread - omit the "network" and "broadcast" statements.

---

### Post by digitldrug on 2009-01-07
Hi Iowan

Wouldn't putting eth1 on a diff subnet cause issues with my ability to access my router/the other computers?

I can however put eth0 on a diff subnet as my ultimate goal it to go gigabit (eth1).

I don't have port 22 open on my router at the moment so I'll have to wait until I get home to try your recommendations. Thank you for your help.

Also, since I manually entered an eth1 entry in the interfaces file, how does the computer know what eth1 is?  I guess I'm asking how ubuntu associates the alias eth1 with the hardware.

Thanks,
 Jordan

---

### Post by Iowan on 2009-01-07
I recommended changing eth1 primarily because eth0 successfully got an IP and eth1 did not... seemed the path of least resistance.  I probably missed (or misread) how you want it set up (sorry).  To find how Ubuntu associates the alias with the interface, use **lshw -C network**. It should give you driver, IP address, MAC address, and several more details.

---

### Post by digitldrug on 2009-01-07
Hey Iowan,

You're a life saver.  I put eth0 on the 192.168.1.x subnet, and eth1 can now access the internet! 

Also thanks for pointing out the "lshw -C network" command.
I'm definitely adding it to my slowly growing command list. :)

The only downside that I have discovered with this config is that eth0 can now no longer access the internet.

1)
If in the future I put ubuntu on my laptop and have both the nic and the wireless connected should I expect the same problem (and therefore can only connect on at a time)?

2)
Is there a way to give both nics internet access through my router? (Dlink 192.168.0.1).

I'm guessing that I'm sol with Question #2 but just figured I'd ask. In either case thank you very much for your help.  On to RAID :)

---

### Post by albinootje on 2009-01-07
> **digitldrug said:**
> 
The only downside that I have discovered with this config is that eth0 can now no longer access the internet.

Erhm, you mean that putting the ethernet cable to eth0, and taking off eth1 you won't have internet ?
The thing is that you only have one default gateway at the time.
But I assume that if you use the hotplug option for the NIC in /etc/network/interfaces that it could work.
In Ubuntu and/or Debian I thought I saw "allow-hotplug eth0" instead of "auto eth0" a while back. 
Not sure whether that option is now obsolete and integrated in the "auto eth0" or not.
> 
1)
If in the future I put ubuntu on my laptop and have both the nic and the wireless connected should I expect the same problem (and therefore can only connect on at a time)?

I've heard that newer versions of Network Manager are suppose to handle the simultaneous use of those connections.

---

### Post by Iowan on 2009-01-07
There are a few threads mentioning problems having wired/wireless active at the same time.  The "old" Network Manager would not manage two interfaces at the same time, but you could manually edit /etc/network/interfaces file to fire up both at the same time.  I don't have a lot of experience with the "new" NM.  It's possible (so I've read) to set Ubuntu up for Internet Connection Sharing using a NIC and wireless card - so both would need to be active... but not in the same subnet.

I'm not familiar with most of the appliance routers... My Freesco router is a '486 computer.  It can house several NIC's and each can (must?) be on separate subnet.  Each subnet can selectively be given/denied internet access.  Though it's only a guess, I suspect your router *might* be capable.

> **digitldrug said:**
> You're a life saver.  I put eth0 on the 192.168.1.x subnet, and eth1 can now access the internet!  Guess I can go to bed happy!

---

