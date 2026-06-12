---
title: "Wifi connection issues in both 10.10 and 11.04"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by xvedejas on 2011-07-08
I bought a laptop back in April, and things had been working just fine since then. The wifi was working perfectly in Ubuntu 10.10, with speed of up to 15Mbps. But a week or two ago, my wifi stopped working correctly, probably due to an update.

The download speed has been very slow, below 1Mbps speeds. There are many frequent disconnects, and times where I cannot connect to my router at all. The shown signal for my wireless is a bit lower than usual, but not by a significant amount. At first I thought it was a problem with my router, so I replaced it, with no luck. Then I read a few forum posts about wifi issues, saying they had been fixed by upgrading to 11.04, which I had not done yet. Now I've upgraded, and my wireless Internet is no better than before.

Here is some relevant information:

```
lspci | grep Network

Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
```

```
sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 00:90:f5:b7:89:a2
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.7 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:56 memory:f6320000-f6323fff ioport:d100(size=128) ioport:d000(size=256) memory:f6310000-f631ffff memory:f6300000-f630ffff
  *-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:90:e0:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=9.221.4.1 build 25532 ip=192.168.1.148 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:54 memory:f6200000-f6201fff

```

Doing a simple ping shows lots of latency. Last time I tried this, most pings were lost as well.

```
ping google.com

PING google.com (74.125.93.147) 56(84) bytes of data.
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=1 ttl=53 time=5055 ms
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=2 ttl=53 time=4217 ms
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=3 ttl=53 time=5528 ms
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=4 ttl=53 time=5058 ms
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=5 ttl=53 time=5035 ms
64 bytes from qw-in-f147.1e100.net (74.125.93.147): icmp_req=6 ttl=53 time=5093 ms

--- google.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 4217.110/4998.073/5528.088/389.085 ms, pipe 6
```

Here are the results of a speedtest: [http://www.speedtest.net/result/1377435587.png](http://www.speedtest.net/result/1377435587.png)
I usually get about 11 down, 3 up. My promised speeds by my ISP are 15 down, 5 up.

---

### Post by xvedejas on 2011-07-09
No help?

---

### Post by bkratz on 2011-07-09
> **xvedejas said:**
> No help?



Perhaps something here?

[http://ubuntuforums.org/showthread.php?t=1656061](http://ubuntuforums.org/showthread.php?t=1656061)

---

### Post by westie457 on 2011-07-09
Hi and I am very happy to say that I do not have this problem as I am using different equipment which has it's own set of problems.

However a suggestion for you as I am doing this blind. Right-click  Network-Manager and select Edit connections.
Select the Wireless tab then select your device and click edit.
In the window that opens take a look at the IPv6 tab. In theory it might need to be set as in the attached pic. If it is the same then you need more help than I can provide. If it is different then no harm will be done if you change it.

Good luck.

---

### Post by xvedejas on 2011-07-09
> **bkratz said:**
> Perhaps something here?

[http://ubuntuforums.org/showthread.php?t=1656061](http://ubuntuforums.org/showthread.php?t=1656061)

No, this didn't help unfortunately. Those with this problem seem to have been limited to about 20Mbps. I am getting under 1Mbps, and in fact it's not the speed that's the main problem, but long stretches of time where it seems that my computer cannot create connections at all.


IPv6 has been set to "ignore" in my wireless settings; I think the problem is more opaque than some network manager setting.

---

### Post by halibaitor on 2011-07-09
"Upgrade" to Ubuntu 10.04.2 and watch your problems go away...  That's how I solved my problems.  :cool:

---

### Post by xvedejas on 2011-07-09
> **halibaitor said:**
> "Upgrade" to Ubuntu 10.04.2 and watch your problems go away...  That's how I solved my problems.  :cool:

I would rather have a solution than just avoiding the problem...

---

