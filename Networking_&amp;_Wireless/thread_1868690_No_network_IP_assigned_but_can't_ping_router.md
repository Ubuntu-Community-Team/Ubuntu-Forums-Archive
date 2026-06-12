---
title: "No network: IP assigned but can't ping router"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by andrewkisielius on 2011-10-24
I'm not sure how to proceed. I'm connected to a wireless network, and assigned an IP address, but pings to the router time out, and nothing beyond is reachable. This was working a few days ago, including after my recent update to 11.10. The only thing I changed manually since then was removing evolution-indicator. I may have installed some updates but don't remember anything major. 

iwconfig shows:
```
lo    no wireless extensions

eth0    no wireless extensions

wlan1    IEEE 802.11bgn  ESSID:"--redacted, but correct--"
    Mode: Managed  Frequency: 2.417 GHz  Access Point:  --also redacted, but correct--
    Bit Rate=120 Mb/s   Tx-Power=20 dBm
    retry  long limit: 7   RGS thr: off   Fragment thr:off
    Power Management: off
    Link Quality=48/70  Signal level=-62 dBm
    Rx invalid nwid:0  Rx invalid crypt: 0  Rx invalid frag: 0
    Tx excessive retries: 45  Invalid misc: 687   Missed beacon:0
```ifconfig wlan1 shows:
```
wlan1    Link encap: Etherenet HWaddr 00:1a:ef:1d:96:36
    inet addr: 10.1.10.13  Bcast 10.1.10.255  Mask 255.255.255.0
    inet6 addr: <long number> Scope:Link
    UP BROADCAST RUNNING PROMISC MULTICAST  MTU: 1500   Metric: 1
    RX packets:10285 errors:0 dropped:0 overruns:0 frame:0
    TX packets:6563 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000
    RX bytes: 6.5MB   TX bytes: 692 KB
```/etc/resolv.conf contains:
```
domain wp.comcast.net
search wp.comcast.net
nameserver 75.75.75.75
nameserver 75.75.76.76
```All of that is pretty much what I expect. I'm submitting this post from another laptop that's happily connected to the network, as are a few other devices. 

A couple other tidbits:

```
$lspci |grep etwork
01:0a.0 Network controller: Ralink corp. RT2800 802.11n PCI
``````
$route -n
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 10.1.10.1 0.0.0.0 UG 0 0 0 wlan1
10.1.10.0 0.0.0.0 255.255.255.0 U 2 0 0 wlan1
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 wlan1
```I'm at a loss here. Any suggestions?

---

### Post by jonobr on 2011-10-25
Can you ping 10.1.10.13?
From there can you ping any other hosts on the same network?

---

### Post by andrewkisielius on 2011-10-29
I thought I said that, but yes, the computer can ping itself, both as 10.1.10.13 and as localhost. But it can't ping anything else on the network.

Here's another data point: I booted with an older kernel, 2.6.38-11, and the connection worked. The problem appears when I boot with 3.0.0-12.


Apologies for the slow response, btw. I didn't realize subscribing to a new thread was no longer default.

---

### Post by Kisil on 2011-11-29
I have this problem using kernels 3.0.0-12-generic and 3.0.0-13-generic, but it goes away when I boot with 2.6.38-11-generic. Does anyone know what else I can do to debug this regression?

---

### Post by dandnsmith on 2011-11-29
I've seen something similar when installing UB 11.10, caused by the system trying to use an IP6 address when the rest of the network (and ISP) are only prepared to handle IP4.
Disabling that allowed the network to be used, and threw up a further 'bug' (which it's unlikely you have) to do with some of the network features involving the use of the r8169 module (see lsmod listing)

---

