---
title: "Intermittent Ethernet connection"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by CalumSult on 2009-07-14
Here's my setup-  9.04 64bit with three wired ethernet connections (eth0-2).  I run two virtualboxes (one Vista, one XP) and each is bridged to one dedicated ethernet connection.  The host uses eth2 (NetworkManager assignes it 'auto').  Periodically on the Ubuntu host the network just hangs.  Firefox can't fetch pages, skype drops, and gwibber can't tweet.  After about 30 seconds or so everything starts working again.  What's weird though is that this doesn't affect either virtual box, everything works on them with no hiccups.  

eth0&1 are built in to the mobo (Realtek chipset), eth2 is a low cost 10/100 pci card.  This is the lspci details of eth2-

```
05:06.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
        Subsystem: ADMtek Device 0570
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at a800 [size=256]
        Memory at fdaff000 (32-bit, non-prefetchable) [size=1K]
        [virtual] Expansion ROM at fd900000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: tulip
        Kernel modules: tulip
```

This is the ifconfig-

```
eth0      Link encap:Ethernet  HWaddr 00:24:1d:1d:bc:79  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe1d:bc79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10709216 (10.7 MB)  TX bytes:1452052 (1.4 MB)
          Interrupt:250 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:24:1d:1d:bc:99  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe1d:bc99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12198 errors:0 dropped:0 overruns:0 frame:0
          TX packets:717 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3123512 (3.1 MB)  TX bytes:121113 (121.1 KB)
          Interrupt:249 Base address:0x8000 

eth2      Link encap:Ethernet  HWaddr 00:1a:70:15:d7:2f  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:70ff:fe15:d72f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:199459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:160002435 (160.0 MB)  TX bytes:22879223 (22.8 MB)
          Interrupt:20 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98623 (98.6 KB)  TX bytes:98623 (98.6 KB)
```

What can I do to troubleshoot this?  I'm a linux newb, especially when google can't answer my questions!  ;)

---

### Post by CalumSult on 2009-07-14
Update- set ping to [www.google.com](www.google.com) and this is what I get-

```
64 bytes from 74.125.95.105: icmp_seq=168 ttl=54 time=72.1 ms
64 bytes from 74.125.95.105: icmp_seq=169 ttl=54 time=69.5 ms
64 bytes from 74.125.95.105: icmp_seq=170 ttl=54 time=60.9 ms
64 bytes from 74.125.95.105: icmp_seq=171 ttl=54 time=59.2 ms
64 bytes from 74.125.95.105: icmp_seq=172 ttl=54 time=89.5 ms
From calum-host.local (192.168.1.100) icmp_seq=203 Destination Host Unreachable
From calum-host.local (192.168.1.100) icmp_seq=204 Destination Host Unreachable
From calum-host.local (192.168.1.100) icmp_seq=205 Destination Host Unreachable
64 bytes from 74.125.95.105: icmp_seq=206 ttl=54 time=64.0 ms
64 bytes from 74.125.95.105: icmp_seq=207 ttl=54 time=59.0 ms
64 bytes from 74.125.95.105: icmp_seq=208 ttl=54 time=58.3 ms

```

...etc etc.  Most of the time it works just fine, then drops for a bit, then picks back up and works again.

---

### Post by superprash2003 on 2009-07-15
well have you tried the same internet connection on another pc? it could be an ISP issue .. a temporary one

---

### Post by CalumSult on 2009-07-15
> **superprash2003 said:**
> well have you tried the same internet connection on another pc? it could be an ISP issue .. a temporary one

Yes, there are multiple PCs (physical and virtual) using this Internet connection with no problems.  I'm going to try swapping the ethernet card out to see if that's the problem, but I hate just throwing money at it without knowing what I'm doing (ok, ethernet cards are cheap :P).

I wish NetworkManager would let you choose which card was 'auto' so I could just switch to one of the other connections and see if the problem persists.  I haven't found a good way of handling multiple ethernet connections in one PC (NetworkManager works, but the not being able to pick which is 'auto' thing kinda stinks), but I'm all ears if you can point me to a better tool.  :)

---

