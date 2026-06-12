---
title: "slow wifi network intel 5100"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by RikoW on 2009-07-23
Hi :)

when I'm on wireless connected to my DSL router, I measure a download speed of about 0.5 Mbit/s. The connection I have allows for 3 Mbit/s, so I'm down by a factor 6! When I connect to the router with a network cable, I actually do get the full bandwidth. 

Also, next to this laptop is another which the same ubuntu version installed, however with a different wifi card. On that one, I also see the full speed. 

So, I suspect it has something to do with either the wifi card driver or the network setup on this machine (using NetworkManager in both cases). 

However, I'm completely clueless as to how to proceed. Here is the essential info:

```
> lspci -v -s 0c:00.0
0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
	Subsystem: Intel Corporation Device 1321
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	Memory at f69fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

```

```
> iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:09:5B:4F:61:BE   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-42 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
> ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:21:5d:e4:24:08  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5dff:fee4:2408/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:9513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9848961 (9.8 MB)  TX bytes:2072772 (2.0 MB)

```

Any ideas would be greatly appreciated.

Thanks and cheers,

               Riko

---

### Post by superprash2003 on 2009-07-23
did you manually play with MTU? have you tried disabling ipv6?

---

### Post by RikoW on 2009-07-23
Hi,

no, i haven't played with MTU. I read, that values higher than 1500 may be a problem and advised to set it to 1492. But the value set is already at 1492.

Also ipv6 I did not disable, since I get full speed on cable. ipv6 should affect wlan and lan in the same way, shouldn't it? I knew once how to do that. Can you remind me?

Thanks,

            Riko

Edit: ipv6 is in fact disabled in firefox only! Would that do as a test?

---

### Post by RikoW on 2009-07-23
Hi :)

googleing some more, I came across this thread, 

[http://ubuntuforums.org/archive/index.php/t-1032617.html]("http://ubuntuforums.org/archive/index.php/t-1032617.html")

which suggested to install the latest wireless drivers via

```
sudo apt-get install linux-backports-modules-jaunty
```

That seems to have fixed my problem. At least now I get the full 3 Mbit/s.

Cheers,

              Riko :popcorn:

---

