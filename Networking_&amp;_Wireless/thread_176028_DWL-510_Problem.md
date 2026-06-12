---
title: "DWL-510 Problem"
date: 2006-05-14
forum: Networking &amp; Wireless
---

### Post by Disabled on 2006-05-14
Ok, yesterday i installed my dwl-510 wireless pci card, using ndiswrapper, and all went straight: i see my ap, and could even ping it :O

Today i was going to configure my pppoe connection to use the modem connected to the ap, but i found that i can't use my card anymore...

I can see it through iwconfig and ifconfig, i've loaded ndiswrapper module, and used "ifconfig wlan0 up", but everytime i try to ping my ap i get this:
```
root@ubuntu:/home/disabled# ping 192.168.0.50
PING 192.168.0.50 (192.168.0.50) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

```

These are the outputs of ifconfig and iwconfig:
```
root@ubuntu:/home/disabled# iwconfig
lo        no wireless extensions.

wlan0     802.11b linked  ESSID:"default"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:80:C8:38:21:0C
          Bit Rate=11 Mb/s   Sensitivity=80/85
          Retry:on   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=34/100  Signal level=-107 dBm  Noise level=-190 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```
root@ubuntu:/home/disabled# sudo ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:40:05:3E:7B:A0
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:5ff:fe3e:7ba0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:319 errors:0 dropped:4 overruns:0 frame:0
          TX packets:454 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28021 (27.3 KiB)  TX bytes:17922 (17.5 KiB)
          Interrupt:177 Memory:e0882f00-e0883000

```
 :) Hope you can help me...

---

