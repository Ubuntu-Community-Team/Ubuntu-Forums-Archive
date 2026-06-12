---
title: "MadWifi doesn't work after kernel rebuild..."
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by Crafty Kisses on 2009-02-13
Hey guys, basically what happened is I had a laptop that was giving me some hardware support issues, so I decided to recompile the kernel in obvious hopes of fixing the problem, well to my surprise it actually did fix the one problem I was having, but yet it created another one. I noticed that I could search for connections, but when I tried connecting, it just wouldn't connect. So I try scanning by doing the following:
```
iwspy ath0 scan
```
The results weren't too good, this is what I got:
```
Interface ath0 doesn't support IP addresses
ath0      Interface doesn't support IP addresses
No valid addresses found : exiting...
```
You may also want to look at the following:
```
ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:11:f5:6c:3a:f8
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
Here's my iwconfig also:
```
iwconfig
lo        no wireless extensions.

bond0     no wireless extensions.

eth0      no wireless extensions.

tunl0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:"coffee1"
          Mode:Managed  Channel:0  Access Point: Invalid
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
I then checked to see if all my modules were in place in the kernel, and it does appear all the modules are there, but if I'm missing something you can have a look:
```
Module                  Size  Used by
mac80211              100842  0
wlan_scan_sta           9728  1
ath_rate_sample        10124  1
ath_pci                81258  0
wlan                  166240  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               189161  3 ath_rate_sample,ath_pci

```
Then here is my Ethernet controller:
```
lspci | grep Ethernet
0000:02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```
I'm pretty lost, I mean I guess I could revert back to the older kernel, but then I would be stuck with my old problem.

---

