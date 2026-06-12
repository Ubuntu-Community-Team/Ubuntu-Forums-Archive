---
title: "RTL-8185 problems"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by irmamo on 2012-03-15
Hello everybody,
[LEFT] 
[/LEFT]
 I've been having an issue with the Realtek RTL-8185 it wont search or connect for wireless connections.
Currently I'm on 9.04 because i read somewhere that the driver rtl8180 works with this version but I 
have not made it work. I was previously on 10.04 and my wifi was working 
fine but I accidently updated with the update manager and that's when the problems began.
[LEFT] 
:confused:[/LEFT]

---

### Post by irmamo on 2012-03-15
```
05:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. 
RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```sudo lshw -C network
```
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wmaster0
       version: 20
       serial: 00:c0:a8:c8:21:7f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 
       mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg

```

---

### Post by irmamo on 2012-03-16
I figured out the issue... and I feel very stupid.  It turns out my wireless radio was off and all I had to do was press FN+F2 and Voila!!!

---

