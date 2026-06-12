---
title: "No Wireless - Edimax 7318UG"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by geezerone on 2008-12-28
Hi

Having been using this wireless adapter for a good few months it has stopped picking up wireless networks since the computer was off for a few weeks.

I did notice that **rt2x_cfg80211** is missing from my working lsmod output which I captured after it was working. Maybe a red herring but you never know.

The output of iwconfig, and lshw -C network below:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=7 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``````
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:3b:ad:52
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.239 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1f:1f:02:dc:7e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```I was working previously by manually configuring /etc/network/interfaces and running /etc/init.d/networking restart in the /etc/rc.local bootup script.

Now though - nothing!

TIA :)

---

