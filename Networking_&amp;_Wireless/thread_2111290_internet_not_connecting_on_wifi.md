---
title: "internet not connecting on wifi"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by jas1291 on 2013-02-01
ok terminal output is this
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"UTStarcom"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:57:F9:71:67   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:9876-2002-28
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:38   Missed beacon:0

---

### Post by ahallubuntu on 2013-02-01
Has it EVER connected?  Or just not now?  A  new install or an old install?

What is the output of these commands:

```
sudo lshw -C network
uname -r
```

---

