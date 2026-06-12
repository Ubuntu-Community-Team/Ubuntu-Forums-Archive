---
title: "static ip on eth3 not working"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by kornphlake on 2009-11-11
Relative newbie here, I've dabbled with Ubuntu for about 6 months but didn't get serious until a few weeks ago.  So far I've been able to find all the answers I've needed, but this one has me stumped.  I'm not even sure what terms to search to find an answer.  Please help, I'm really beyond my understanding of Linux and networking at this point.

I'm working on setting up an Ubuntu 8.04 box for a proxy using squid, dhcp3-server, dansguardian and firestarter.  It worked a few days ago, but then I rebooted and eth3 doesn't want to register a static IP correctly so the dhcp server won't start correctly and neither will firestarter.  The interfaces are named eth2, plugged into the modem and eth3 plugged into the switch.

I assume the important information is as follows:

```

$ sudo gedit /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

iface eth2 inet dhcp
auto eth2



#Static configuration for eth3
iface eth3 inet static
address 192.168.0.1    
netmask 225.225.225.0
network 192.168.0.0
broadcast 192.168.0.255

```What's increasingly frustrating is that the static ip for eth3 isn't assigned as shown above

```

$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:40:ca:41:3e:e9  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe41:3ee9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5837 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4333219 (4.1 MB)  TX bytes:734426 (717.2 KB)
          Interrupt:10 Base address:0xd400 

eth3      Link encap:Ethernet  HWaddr 00:48:54:65:f8:5e  
          inet6 addr: fe80::248:54ff:fe65:f85e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5366 (5.2 KB)  TX bytes:20044 (19.5 KB)
          Interrupt:11 Base address:0xd000 

eth3:avahi Link encap:Ethernet  HWaddr 00:48:54:65:f8:5e  
          inet addr:169.254.7.214  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8535657 (8.1 MB)  TX bytes:8535657 (8.1 MB)

```Eth2 seems to be working just fine, it accepts the ip from the router, for whatever reason the IP for eth3 is something completely different than what's defined in the /etc/network/interfaces file. Not to mention the fact that eth3 seems to be showing twice.

I thought I'd finally gotten everything working and just wanted to make sure all the services were starting automatically after a reboot and this is what happened, it's very frustrating.  Please help!

---

### Post by DGortze380 on 2009-11-11
> **kornphlake said:**
> Relative newbie here, I've dabbled with Ubuntu for about 6 months but didn't get serious until a few weeks ago.  So far I've been able to find all the answers I've needed, but this one has me stumped.  I'm not even sure what terms to search to find an answer.  Please help, I'm really beyond my understanding of Linux and networking at this point.

I'm working on setting up an Ubuntu 8.04 box for a proxy using squid, dhcp3-server, dansguardian and firestarter.  It worked a few days ago, but then I rebooted and eth3 doesn't want to register a static IP correctly so the dhcp server won't start correctly and neither will firestarter.  The interfaces are named eth2, plugged into the modem and eth3 plugged into the switch.

I assume the important information is as follows:

```

$ sudo gedit /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

iface eth2 inet dhcp
auto eth2



#Static configuration for eth3
iface eth3 inet static
address 192.168.0.1    
netmask 225.225.225.0
network 192.168.0.0
broadcast 192.168.0.255

```What's increasingly frustrating is that the static ip for eth3 isn't assigned as shown above

```

$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:40:ca:41:3e:e9  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe41:3ee9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5837 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4006 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4333219 (4.1 MB)  TX bytes:734426 (717.2 KB)
          Interrupt:10 Base address:0xd400 

eth3      Link encap:Ethernet  HWaddr 00:48:54:65:f8:5e  
          inet6 addr: fe80::248:54ff:fe65:f85e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5366 (5.2 KB)  TX bytes:20044 (19.5 KB)
          Interrupt:11 Base address:0xd000 

eth3:avahi Link encap:Ethernet  HWaddr 00:48:54:65:f8:5e  
          inet addr:169.254.7.214  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8535657 (8.1 MB)  TX bytes:8535657 (8.1 MB)

```Eth2 seems to be working just fine, it accepts the ip from the router, for whatever reason the IP for eth3 is something completely different than what's defined in the /etc/network/interfaces file. Not to mention the fact that eth3 seems to be showing twice.

I thought I'd finally gotten everything working and just wanted to make sure all the services were starting automatically after a reboot and this is what happened, it's very frustrating.  Please help!

You need 

```

auto eth3

```

before the iface line if you'd like it come up automatically, otherwise you'll need to bring it up manually

```

sudo ifup eth3

```

---

### Post by kornphlake on 2009-11-11
I'll give that a try, thanks:)

---

### Post by kornphlake on 2009-11-12
adding 
```

auto eth3

```
and adjusting some settings in dhcp3 to get the ip of eth3 straightened out fixed everything.  That one line of code was the one I just wasn't seeing.  Thanks!

---

