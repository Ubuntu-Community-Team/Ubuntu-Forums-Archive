---
title: "Wireless suddenly stopped working"
date: 2011-02-07
forum: Networking &amp; Wireless
---

### Post by Canadian_Pirate on 2011-02-07
Hey
This may have been covered before, and I apologise if it has.
I have been using Ubuntu for a while on my Lenovo s10-3t (Atheros AR9285 wireless adapeter) with the wireless working fine. Suddenly it just stopped working. I went to Windows 7, and it did not work. I then tried MeeGo (previously installed with wireless working), and it did not work. Here are various outputs of commands:
```
$ lspci
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:db:ac:8f  
          inet addr:192.168.75.49  Bcast:192.168.75.255  Mask:255.255.255.0
          inet6 addr: fe80::ca0a:a9ff:fedb:ac8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5856097 (5.8 MB)  TX bytes:1037800 (1.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12409 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5541924 (5.5 MB)  TX bytes:5541924 (5.5 MB)


```

---

