---
title: "Net connection slowness: timeout?"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by rosslaird on 2009-07-25
I am sure that this has been asked and answered in other threads, but a dedicated search does not produce the solution. So: replacing my router seems to have introduced a delay in net connection for my Ubuntu Jaunty laptop (the Mac on the same network has no connection delay). In my browser, email, and ssh, there is a delay of anywhere between 10 and 20 seconds before net connections are made. I have tried to discover what is causing this (and I have tried, without success, to speed up Firefox using various methods). ipv6 is off. Here's what dmesg says:

```

[   51.953305] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  950.136259] wlan0: direct probe to AP 00:22:6b:79:c7:b1 try 1
[  950.336160] wlan0: direct probe to AP 00:22:6b:79:c7:b1 try 2
[  950.536149] wlan0: direct probe to AP 00:22:6b:79:c7:b1 try 3
[  950.736155] wlan0: direct probe to AP 00:22:6b:79:c7:b1 timed out
[  969.774754] wlan0: direct probe to AP 00:22:6b:79:c7:b1 try 1
[  969.972084] wlan0: direct probe to AP 00:22:6b:79:c7:b1 try 2
[  970.172138] wlan0: direct probe to AP 00:22:6b:79:c7:b1 try 3
[  970.372136] wlan0: direct probe to AP 00:22:6b:79:c7:b1 timed out
[ 1979.077509] CE: hpet increasing min_delta_ns to 15000 nsec
[ 4392.248135] CE: hpet increasing min_delta_ns to 22500 nsec
[ 9596.860976] ath5k phy0: unsupported jumbo
[20586.114983] ip_tables: (C) 2000-2006 Netfilter Core Team
[69110.708133] CE: hpet increasing min_delta_ns to 33750 nsec

```

Is that "timed out" message the problem? An, if so, how do I fix it? (I have also added the opendns servers to my router and my laptop without success for the current problem).

Thanks in advance for any help.

Ross

EDIT:

Actually, wlan0 is the wireless connection, yes? The slow connection does happen there, but when I ran dmseg for this problem, I was plugged in via cable and the wireless was not connected. So, this may be an entirely separate issue. Feedback still welcome.

---

### Post by superprash2003 on 2009-07-26
post output of
1)ifconfig
2)iwconfig

---

### Post by rosslaird on 2009-07-26
ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1e:37:d0:77:8a  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:18cf:34fc:0:21e:37ff:fed0:778a/64 Scope:Global
          inet6 addr: fe80::21e:37ff:fed0:778a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:684586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:508995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:720806689 (720.8 MB)  TX bytes:81422857 (81.4 MB)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69953 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:337830507 (337.8 MB)  TX bytes:337830507 (337.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:7c:0e:da  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-E1-7C-0E-DA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

---

### Post by superprash2003 on 2009-07-28
hmm..these outputs show that your wlan0 isnt connected to any wifi router at all!!

---

### Post by rosslaird on 2009-07-28
Yes, that's correct. My wireless is not currently connected. It's eth0 I'm working form (though, when the wireless is connected, both are slow). I wonder if this could be part of the problem: the Mask shown by ifconfig is 255.255.255.0 , whereas the Subnet Mask shown on the router's admin pages is 255.255.252.0.

---

### Post by superprash2003 on 2009-07-29
you could try disconnecting eth0 and trying only wlan0 and then post those outputs

---

### Post by rosslaird on 2009-07-29
With eth0 unplugged and wireless active:
ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1e:37:d0:77:8a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:880 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:371741 (371.7 KB)  TX bytes:371741 (371.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:7c:0e:da  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:18cf:34fc:0:21f:e1ff:fe7c:eda/64 Scope:Global
          inet6 addr: fe80::21f:e1ff:fe7c:eda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10910707 (10.9 MB)  TX bytes:8181920 (8.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-E1-7C-0E-DA-65-64-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"abydos"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:6B:79:C7:B1   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=39/100  Signal level:-71 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

While composing this post, it took 19 seconds for Firefox to complete "Looking up" the forum.

---

### Post by superprash2003 on 2009-07-30
try disabling ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by rosslaird on 2009-07-30
> **superprash2003 said:**
> try disabling ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Already done.

I have also noticed that the slowness persists across connections. So, when I connect from my university, for example (eth0 or wireless), I have the same problem. I have also experienced nm-applet freezing the whole system, and this may or not be related to my current issue. The freezing is non-recoverable (I cannot restart the X server, or jump to a console, or get anything to respond), and it always happens when nm-applet is trying to connect. It does not happen every time -- about 20 per cent of the time, I'd say. I know that there have been problems with nm-applet and /etc/hosts, so just for the hell of it, here's my hosts file as well:

```

127.0.0.1	localhost
127.0.1.1	rosslaird

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by superprash2003 on 2009-07-31
well are you sure you've already disabled ipv6? cause your ifconfig output still shows an ipv6 address

---

### Post by rosslaird on 2009-07-31
In the ipv6 thread there is a section on testing to see whether ipv6 is enabled or disabled. The indicated command is:

```
lsmod | grep inet6 
```

When I run that command, I get no output, which the thread says is an indicator that ipv6 is disabled on my system. Is that not correct?

---

### Post by Loosewheel on 2009-08-01
> **rosslaird said:**
> Yes, that's correct. My wireless is not currently connected. It's eth0 I'm working form (though, when the wireless is connected, both are slow). I wonder if this could be part of the problem: the Mask shown by ifconfig is 255.255.255.0 , whereas the Subnet Mask shown on the router's admin pages is 255.255.252.0.

rosslaird, did you try to set the router up with 255.255.255.0?
That kinda looks like it might be the problem. Here's a link:
[http://en.wikipedia.org/wiki/Subnet_mask](http://en.wikipedia.org/wiki/Subnet_mask)

I'm curious as to what you found out.

---

### Post by rosslaird on 2009-08-01
OK, progress. The method that I showed above for discovering whether or not ipv6 is enabled (the method shown on the Ubuntu wiki) does not give a correct result -- at least on my system, which is Jaunty with the 2.6.28 kernel. The method that does work is this:

```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```

If this shows a 1, ipv6 is disabled; it if shows a 0, ipv6 is enabled. To disable it, I used:

```
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
```

The above caused my system to return to proper (ie. fast) DNS resolution. I am still working on the default gateway issue.

---

