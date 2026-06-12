---
title: "streaming from backend kills network"
date: 2008-04-30
forum: Mythbuntu
---

### Post by Eternal Ponderer on 2008-04-30
Hopefully someone here can help, I've gone through quite a bit to find an answer, but have so far come up empty.

I've run Myth in a slave/masterslave environment for quite some time.  I do not think my issue is necessarily myth specific, so much as it is Ubuntu 8.04 specific, however, I could be wrong.  My belief stems from having no problems in 7.10 running the latest .21 fixes, this all started on 8.04...

I have been able to reproduce this problem with multiple mythbuntu installs on 2 different motherboards/chipsets and 3 network adapters.

To simplify my setup, I stripped my backend to include only one tuner: a pcTV HD-3000.  The mythbuntu-desktop is a standard install, nothing fancy.

When I go to my frontend to watch a show while the backend is recording, the backend completely fails and falls off the network.

my eth card...
```

$ dmesg |grep eth
[   23.155351] eth0: VIA Rhine II at 0xe6001000, 00:11:5b:4b:b0:34, IRQ 18.
[   23.156063] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[   32.051176] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   44.649228] eth0: no IPv6 routers present

```

Everything is groovy at this point, now I'll goto the frontend and try to watch a show on the backend while it is recording.  Now, the backend reports:

```

[  326.982127] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  326.982792] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  332.971347] NETDEV WATCHDOG: eth0: transmit timed out
[  332.971500] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  332.972170] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

```

Wow, it seems my network disappeared?  But, it also says it came back up, notice the 'link up'  This entire time I didn't unplug anything or physically change anything.

My gateway is gone..
```

$ ping 192.168.15.1
PING 192.168.15.1 (192.168.15.1) 56(84) bytes of data.

--- 192.168.15.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2010ms

```

It sees itself...
```

$ ping 192.168.15.123
PING 192.168.15.123 (192.168.15.123) 56(84) bytes of data.
64 bytes from 192.168.15.123: icmp_seq=1 ttl=64 time=0.039 ms
64 bytes from 192.168.15.123: icmp_seq=2 ttl=64 time=0.050 ms

```

Try resetting eth0...
```

$ sudo ifdown eth0
$ sudo ifup eth0

```

Nope, network still dead...
```

$ ping 192.168.15.1
PING 192.168.15.1 (192.168.15.1) 56(84) bytes of data.
From 192.168.15.123 icmp_seq=1 Destination Host Unreachable
From 192.168.15.123 icmp_seq=4 Destination Host Unreachable
From 192.168.15.123 icmp_seq=5 Destination Host Unreachable

```

At this point, I literally can't get the interface back online.  I don't know where else to look or what else I can do.  Rebooting brings it back up.  I've done all the stupid troubleshooting of cables, switches, heck I've even swapped mobo's and nic's, and the problem persists. I can browse the backend recorded shows and watch the small preview window from the frontend for as long as I want.  But, as soon as I hit a show to watch it (ie, send a large amount of network data as these are HD frames), the backend network goes away.

Help anyone?  Thanks in advance.

---

### Post by mark467 on 2008-09-24
Did you find any solution yet. I think I am getting the same. It only happens to me in the recordings menu. I can watch a dvd iso over it no problem but when i go to recordings menu my backend link dies. Mine does come back up but will die again if i stay in the recordings menu. What info can I give you that may help troubleshoot this.

---

