---
title: "wireless  - access point not associated"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by steph7 on 2010-10-29
hi,
I have the following problem.

I tried
```
sudo iwlist wlan0 scan
```
and I've found my ap, and the essid, but executing:

```
sudo iwconfig wlan0 mode managed channel 1 essid XXXXX
```

```
iwconfig wlan0
```

the AP still is not associated:

```
wlan0     802.11bg  ESSID:"XXXX"  Nickname:"XXXXX"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:48 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

what can I try now?
thanks in advance

HELP!!

---

### Post by steph7 on 2010-10-30
help! thanksss

---

### Post by chili555 on 2010-10-30
First, getting a connection using manual methods, iwconfig, et al, is very difficult to impossible with Network Manager installed and running.

Second, it wants to know how you wish to connect, either static:```
sudo ifconfig 192.168.1.86 up
```Or DHCP:```
sudo dhclient wlan0
```If Network Manager is running, expect dhclient to time out; NM will not give up the helm easily.

If you use static methods, you will be responsible to set up /etc/resolv.conf.

---

