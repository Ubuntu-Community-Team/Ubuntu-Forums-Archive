---
title: "Internet disconnection on Ubuntu 10.10"
date: 2010-09-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sarafsaurabh on 2010-09-27
After installing Ubuntu 10.10 Maverick Beta, my internet connection keeps on connecting and disconnecting every 10-15 seconds. Although the network-manager icon shows that the connection is on, the browser itself keeps on rotating the busy icon. The connection disconnection cycle keeps on continuing forever.

I have disabled ipv6 system-wide. This problem happens on Ethernet as well as on Wireless.

---

### Post by davrosuk on 2010-09-27
Can you be a little more specific? How are you connected to the internet? Have you tried pinging, for example, Google to see if you are getting drop outs.

I'll be honest it doesn't sound like an IP issue to me...

---

### Post by sarafsaurabh on 2010-09-27
As long as the connection is fine it pings well.

PING [www.google.com]("http://www.google.com") (74.125.19.103) 56(84) bytes of data.
64 bytes from nuq04s01-in-f103.1e100.net (74.125.19.103): icmp_req=1 ttl=55 time=3.82 ms
64 bytes from nuq04s01-in-f103.1e100.net (74.125.19.103): icmp_req=2 ttl=55 time=2.98 ms
64 bytes from nuq04s01-in-f103.1e100.net (74.125.19.103): icmp_req=3 ttl=55 time=3.78 ms
64 bytes from nuq04s01-in-f103.1e100.net (74.125.19.103): icmp_req=4 ttl=55 time=3.64 ms


Once the connection drops, the pining process just hangs with no output and then dies out with error "unknown host google.com"

---

### Post by davrosuk on 2010-09-27
Try pinging the IP directly rather than hostname. Does that make a difference?

---

### Post by sarafsaurabh on 2010-09-28
It still stalls the ping command if I try to ping the IP directly. Only difference being this time it wont show the "unknown host" error.

> **davrosuk said:**
> Try pinging the IP directly rather than hostname. Does that make a difference?

---

### Post by cariboo on 2010-09-28
Does anything show up in dmesg, when the connection drops?

---

### Post by sarafsaurabh on 2010-09-28
I did a diff between the outputs of dmesg when the connection is on and off. But the diff showed no results.

Let me know if the output of dmesg will be of any help. I am not sure if its ok to paste a long post here. I can paste the output if required.


> **cariboo907 said:**
> Does anything show up in dmesg, when the connection drops?

---

### Post by cariboo on 2010-09-28
Just copy and paste the section where wireless connects and disconnects. Just for lol's, this is at the end of dmesg:

```
[   16.590064] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   16.590258] eth0: no link during initialization.
[   16.591022] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

even though I'm connected.

---

### Post by sarafsaurabh on 2010-09-28
These are the last few lines of my dmesg.

[   21.077234] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   21.187793] ppdev: user-space parallel port driver
[   21.355582] dell-wmi: Received unknown WMI event (0x11)
[   21.372208] Skipping EDID probe due to cached edid
[   21.869713] Skipping EDID probe due to cached edid
[   22.023752] Skipping EDID probe due to cached edid
[   22.741931] Skipping EDID probe due to cached edid
[   22.894134] Skipping EDID probe due to cached edid
[   23.153717] Skipping EDID probe due to cached edid
[   23.289705] Skipping EDID probe due to cached edid
[   23.449887] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   24.224558] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   24.224561] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   24.224562] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   24.224563] vboxdrv: the usage of hardware performance counters by
[   24.224564] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   24.224568] vboxdrv: Found 2 processor cores.
[   24.224979] vboxdrv: fAsync=0 offMin=0x1a2 offMax=0x1c21
[   24.225456] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   24.225459] vboxdrv: Successfully loaded version 3.2.6 (interface 0x00140001).
[   25.856209] CE: hpet increased min_delta_ns to 7500 nsec
[   26.545255] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   30.008629] Skipping EDID probe due to cached edid
[   30.145641] Skipping EDID probe due to cached edid
[   30.297833] Skipping EDID probe due to cached edid
[   36.520883] Skipping EDID probe due to cached edid


Unfortunately the disconnection interval(25-30 sec) is longer than the connection interval(3-5 secs) :-(

---

### Post by cariboo on 2010-09-28
Have you tried the Intel e1000 driver instead of the e1000e? Open a terminal and type:

```
sudo rmmod e1000e
```

then insert the e1000:

```
sudo modprobe e1000
```

See if that makes a difference.

If it does make a difference, you can blacklist the e1000e driver, and remove the e1000 from the blacklist.

---

### Post by sarafsaurabh on 2010-10-04
e1000 does not seem to work.

I am still loosing packets:


saurabh@riva:~$ ping 74.125.19.104
PING 74.125.19.104 (74.125.19.104) 56(84) bytes of data.
64 bytes from 74.125.19.104: icmp_req=9 ttl=55 time=3.68 ms
64 bytes from 74.125.19.104: icmp_req=10 ttl=55 time=3.53 ms
64 bytes from 74.125.19.104: icmp_req=11 ttl=55 time=3.34 ms
64 bytes from 74.125.19.104: icmp_req=12 ttl=55 time=3.57 ms
64 bytes from 74.125.19.104: icmp_req=13 ttl=55 time=5.79 ms
64 bytes from 74.125.19.104: icmp_req=14 ttl=55 time=6.22 ms
64 bytes from 74.125.19.104: icmp_req=15 ttl=55 time=33.2 ms
64 bytes from 74.125.19.104: icmp_req=16 ttl=55 time=6.88 ms
64 bytes from 74.125.19.104: icmp_req=17 ttl=55 time=5.30 ms
64 bytes from 74.125.19.104: icmp_req=18 ttl=55 time=3.27 ms
64 bytes from 74.125.19.104: icmp_req=19 ttl=55 time=3.43 ms
64 bytes from 74.125.19.104: icmp_req=20 ttl=55 time=4.25 ms
64 bytes from 74.125.19.104: icmp_req=21 ttl=55 time=4.42 ms
64 bytes from 74.125.19.104: icmp_req=22 ttl=55 time=3.40 ms
64 bytes from 74.125.19.104: icmp_req=23 ttl=55 time=3.60 ms
64 bytes from 74.125.19.104: icmp_req=24 ttl=55 time=3.51 ms
64 bytes from 74.125.19.104: icmp_req=46 ttl=55 time=6.13 ms
64 bytes from 74.125.19.104: icmp_req=47 ttl=55 time=3.17 ms
64 bytes from 74.125.19.104: icmp_req=48 ttl=55 time=7.32 ms
64 bytes from 74.125.19.104: icmp_req=49 ttl=55 time=3.43 ms
64 bytes from 74.125.19.104: icmp_req=50 ttl=55 time=3.27 ms
64 bytes from 74.125.19.104: icmp_req=51 ttl=55 time=3.33 ms
64 bytes from 74.125.19.104: icmp_req=52 ttl=55 time=3.26 ms
64 bytes from 74.125.19.104: icmp_req=53 ttl=55 time=3.48 ms
64 bytes from 74.125.19.104: icmp_req=54 ttl=55 time=5.51 ms
64 bytes from 74.125.19.104: icmp_req=55 ttl=55 time=3.44 ms
64 bytes from 74.125.19.104: icmp_req=56 ttl=55 time=4.02 ms
64 bytes from 74.125.19.104: icmp_req=57 ttl=55 time=3.50 ms
64 bytes from 74.125.19.104: icmp_req=58 ttl=55 time=3.86 ms
64 bytes from 74.125.19.104: icmp_req=59 ttl=55 time=3.19 ms
64 bytes from 74.125.19.104: icmp_req=60 ttl=55 time=3.22 ms
64 bytes from 74.125.19.104: icmp_req=61 ttl=55 time=31.0 ms
64 bytes from 74.125.19.104: icmp_req=87 ttl=55 time=3.18 ms
64 bytes from 74.125.19.104: icmp_req=88 ttl=55 time=3.61 ms
64 bytes from 74.125.19.104: icmp_req=89 ttl=55 time=3.57 ms
64 bytes from 74.125.19.104: icmp_req=90 ttl=55 time=3.29 ms
64 bytes from 74.125.19.104: icmp_req=112 ttl=55 time=3.18 ms
64 bytes from 74.125.19.104: icmp_req=113 ttl=55 time=3.10 ms
64 bytes from 74.125.19.104: icmp_req=114 ttl=55 time=3.15 ms
64 bytes from 74.125.19.104: icmp_req=115 ttl=55 time=3.04 ms
64 bytes from 74.125.19.104: icmp_req=116 ttl=55 time=3.02 ms
64 bytes from 74.125.19.104: icmp_req=117 ttl=55 time=3.45 ms
64 bytes from 74.125.19.104: icmp_req=118 ttl=55 time=3.48 ms
64 bytes from 74.125.19.104: icmp_req=119 ttl=55 time=3.70 ms
64 bytes from 74.125.19.104: icmp_req=120 ttl=55 time=3.03 ms
64 bytes from 74.125.19.104: icmp_req=121 ttl=55 time=3.63 ms
64 bytes from 74.125.19.104: icmp_req=122 ttl=55 time=3.30 ms
64 bytes from 74.125.19.104: icmp_req=123 ttl=55 time=3.27 ms
64 bytes from 74.125.19.104: icmp_req=124 ttl=55 time=3.18 ms
64 bytes from 74.125.19.104: icmp_req=146 ttl=55 time=3.14 ms
64 bytes from 74.125.19.104: icmp_req=147 ttl=55 time=3.32 ms
64 bytes from 74.125.19.104: icmp_req=148 ttl=55 time=3.53 ms
64 bytes from 74.125.19.104: icmp_req=175 ttl=55 time=3.27 ms
64 bytes from 74.125.19.104: icmp_req=176 ttl=55 time=4.36 ms
64 bytes from 74.125.19.104: icmp_req=177 ttl=55 time=3.45 ms
64 bytes from 74.125.19.104: icmp_req=178 ttl=55 time=3.32 ms
64 bytes from 74.125.19.104: icmp_req=179 ttl=55 time=3.73 ms
64 bytes from 74.125.19.104: icmp_req=180 ttl=55 time=3.11 ms
64 bytes from 74.125.19.104: icmp_req=181 ttl=55 time=3.65 ms
64 bytes from 74.125.19.104: icmp_req=182 ttl=55 time=3.30 ms
64 bytes from 74.125.19.104: icmp_req=183 ttl=55 time=3.19 ms
64 bytes from 74.125.19.104: icmp_req=184 ttl=55 time=3.21 ms
64 bytes from 74.125.19.104: icmp_req=185 ttl=55 time=7.02 ms
^C
--- 74.125.19.104 ping statistics ---
[B]194 packets transmitted, 63 received, 67% packet loss, time 193762ms
rtt min/avg/max/mdev = 3.021/4.708/33.200/5.069 ms[/B]




> **cariboo907 said:**
> Have you tried the Intel e1000 driver instead of the e1000e? Open a terminal and type:

```
sudo rmmod e1000e
```then insert the e1000:

```
sudo modprobe e1000
```See if that makes a difference.

If it does make a difference, you can blacklist the e1000e driver, and remove the e1000 from the blacklist.

---

