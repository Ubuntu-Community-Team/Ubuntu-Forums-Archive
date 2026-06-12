---
title: "CAN connect to other computers BUT NOT router or internet - Ubuntu 10.04"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by ironwolfe on 2011-01-03
Situation: Dad's Computer

- CAN connect to other computers - ssh and vnc over the home network (via D-link 524 router).
- CAN get an IP address via DHCP
- CANNOT get internet connections - including router at 192.168.0.1
- CANNOT even ping router (but I get an IP address - weird)
- Other computers on the network CAN access internet
- Live CD could not access internet


results of ifconfig

```
doug@doug-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:21:15:91:1c  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fe15:911c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:209006 (209.0 KB)  TX bytes:225401 (225.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102566 (102.5 KB)  TX bytes:102566 (102.5 KB)

```

lspci -v results

```
 03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
	Subsystem: Elitegroup Computer Systems Device 8056
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at fddfc000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at ac00 [size=256]
	[virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: sky2
	Kernel modules: sky2


```

I am wondering if his ISP could be doing this - he has received a warning letter about bitorrent.  Could the isolate a single computer behind a NAT router?

This is the results from dmesg:

```
doug@doug-desktop:~$ dmesg | grep eth0
[    0.833897] sky2 eth0: addr 00:19:21:15:91:1c
[   19.212986] sky2 eth0: enabling interface
[   19.217462] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.122262] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   22.122462] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.985011] eth0: no IPv6 routers present

```

I have tried:

- to set proxy settings as "Direct internet connection"
- disconnecting power to (including 30 sec wait): modem, router, computer + unplugging ethernet from computer
- Live CD (he only had an old one 7.10) which also didn't connect to internet, but as I am remote, I couldn't do any more.  We are downloading a 10.04.1 iso for him to burn tomorrow, and will try that again.
- Uninstalled Crashplan which was the last software that we installed (and it was working ok).

I am currently ssh'ing into another computer on the network that IS working, and then ssh'ing into my Dad's computer - including a VNC session (tunneled through both machines and router).

I'll buy a beer if someone can help me figure this one out. [mailed voucher of course] ;)

Thanks for any help in this conundrum.  I am not even sure if re-installing ubuntu will help.  I suspect it must be hardware.

---

### Post by PatchesTheCaveman on 2011-01-03
Hi ironwolfe.  Happy New Year!

Run this and copy/paste the result:
```
ip route show
```

---

### Post by ironwolfe on 2011-01-03
> **PatchesTheCaveman said:**
> Hi ironwolfe.  Happy New Year!

Run this and copy/paste the result:
```
ip route show
```

Results:

```
doug@doug-desktop:~$ ip route show
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.101  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.0.1 dev eth0 
default via 192.168.0.1 dev eth0  proto static 
```

Thanks for your interest - and happy new year back!

---

### Post by ironwolfe on 2011-01-03
I should have also mentioned that I tried:

- Manualing entering static IP (no DHCP) and DNS settings.  No luck; same results.

---

### Post by PatchesTheCaveman on 2011-01-03
You shouldn't have two.  (But that ought to be harmless.)  Try deleting both:
```
sudo ip route del default proto static
sudo ip route del default
```

Then add back one:
```
sudo ip route add default via 192.168.0.1 proto static
```

---

### Post by ironwolfe on 2011-01-03
I figured it out - after sleeping on it - I realized it must be the router.

I accessed the router via my mom's computer - using X port forwarding of firefox... (ugh old computer) deleted the static ip for the trouble computer - it was accessing the wrong MAC address (weird...).  It then worked.

---

