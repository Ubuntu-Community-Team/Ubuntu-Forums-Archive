---
title: "Very high ping using DWA-140 in Ubuntu Server 11.10"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by Michael_BoG on 2011-12-21
Hi guys,

Im getting a insanely high ping using the DWA-140 in Ubuntu Server with the rt2800usb drivers. The rest of the network (all Windows) is fine. No idea whats wrong here.

```

Svar fra 192.168.0.111: byte=32 tid=269ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=88ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=213ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=31ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=641ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=280ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=305ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=123ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=248ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=375ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=250ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=421ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=46ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=58ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=104ms TTL=64
Svar fra 192.168.0.111: byte=32 tid=1ms TTL=64

```

```

root@ubuntu:/home/mike# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Johansen_Nett"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 34:21:09:06:26:AE
          Bit Rate=120 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=47/70  Signal level=-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:611  Invalid misc:7   Missed beacon:0

```

```

root@ubuntu:/home/mike# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4050 (4.0 KB)  TX bytes:4050 (4.0 KB)

wlan0     Link encap:Ethernet  HWaddr f0:7d:68:fb:0d:50
          inet addr:192.168.0.111  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::f27d:68ff:fefb:d50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36606403 (36.6 MB)  TX bytes:1885658 (1.8 MB)

```

Any ideas?

---

### Post by Michael_BoG on 2011-12-21
Nevermind, solved by disabling power management.

---

