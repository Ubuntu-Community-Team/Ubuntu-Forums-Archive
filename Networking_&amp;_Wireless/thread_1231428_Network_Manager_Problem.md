---
title: "Network Manager Problem"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by Topher88 on 2009-08-04
Installed studio and went through a big ordeal trying to get the internet working.  I finally got it working and downloaded Network Manager, and worked alright at first, but it's acting weird now...  At first it said that my wired connection was working and the wireless device had not been managed, but after installing updates, it now says that my Wired Network isn't managed and it shows available wireless networks, but none of the wireless networks actually connect and I can still only get Internet with an Ethernet cable...  So, it's like it's backwards, lol; it says that wireless works but it doesn't, and it says that wired doesn't work, but it does...

IFconfig:
```

chris@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:d8:5c:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:25:56:5c:58:14  
          inet6 addr: fe80::225:56ff:fe5c:5814/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:8b:d8:5c:c7  
          inet addr:169.254.9.21  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:249 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1026 (1.0 KB)  TX bytes:1026 (1.0 KB)

```

LSHW:
```

*-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:5c:58:14
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:d8:5c:c7
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=139.78.114.227 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:88:2e:90:e6:c8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by Topher88 on 2009-08-04
UPDATE:  

Huh...  I found out that my wireless had been disabled (via the button on my PC), but I don't know for how long...   I enabled it and tried again and now it works, but what I don't get is that, if it were disabled, how could it have detected wireless networks?  Does being disabled mean it can detect them but I just can' access them?

Well, anyway...  NM still says that my wired device hasn't been managed, but it still works when plugged in.  Minor fluke, I guess...  it doesn't really matter so long as it works...

---

### Post by Iowan on 2009-08-04
There may be a couple of ways to fix the "unmanaged" message. If you're happy with "working", that's the easiest fix.

---

### Post by Topher88 on 2009-08-04
> **Iowan said:**
> There may be a couple of ways to fix the "unmanaged" message. If you're happy with "working", that's the easiest fix.

If you have any ideas, by all means throw them at me and I'll see what i can do.

---

### Post by Topher88 on 2009-08-04
And besides...  Now that I've gotten home and actually been able to try it out on my own wireless network, I'm finding that, while it does work, it's a lot slower and more laggy than it is in my Vista partition.  It also has to disconnect/reconnect a lot...  So, if there are any ideas that you have in that regard as well...  Let me know.

---

### Post by Iowan on 2009-08-04
Just guessing, but you probably have a definition for your wired  (unmanaged) network in */etc/network/interfaces*.  One method involves commenting out the definition and setting it up via Network Manager.
  Another method involves editing */etc/NetworkManager/nm-system-settings.conf*. There are some other threads that have better explanation of how/where to change managed=true. Seems like Network Manager only wants to manage one interface at a time, but this laptop can connect (via NM) to either wired or wireless.

---

### Post by Topher88 on 2009-08-05
UPDATE:  Network Manager appears to be working (it no longer says that my wired network is not managed) properly now, but it's still performing poorly (slow, dropped connections, and for some reason my wireless is automatically disabled upon login).  I've been working to fix a different problem with my system freezing, and I wanted to fix that first before messing with this problem any more.  Switching to the generic kernel from the rt kernel seems to have fixed the freezing problem, so now I can move back to this.

---

### Post by Topher88 on 2009-08-06
So does anyone have any ideas on how to speed up the wireless and make it more stable?  

I found out today that, for some reason, it works just fine at my girlfriend's house, but not so much on my college campus or at my own hose.  At my house, it's very unstable; it is constantly dropping the connection and re-connecting and it is very slow and laggy, and I cannot run any kind of updates or download anything because it takes too long.  It is about the same on campus if I can even get it connected there at all; sometimes it works, sometimes it doesn't.  But like I said, it seems to work the best at my girlfriend's.  The wireless works great at all three of these locations on the same computer in Vista.

---

