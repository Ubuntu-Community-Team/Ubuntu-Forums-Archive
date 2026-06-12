---
title: "private wifi works, hotspot doesn't"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by AKoine on 2010-02-23
Hello everyone,

I have an odd problem :

On my dell mini9 using Karmic netbook-remix, I can't connect to hotspots, whereas my private wifi network (using WEP), at home, works like a charm.

I can see the wifi networks around, no probs. But when I try to connect to one of my ISP hotspot (including the one broadcasted by my own modem/wifi router), the network-manager icon turns for a while then stops saying "not connected". I suppose it hangs on acquiring IP and eventually resigns.

I've tried with my ISP hotspots (Free, I'm french) and an other ISP, to no avail, even though it used to work with Jaunty.
I tried using Wicd instead of network-manager : it work once (I got an IP, launched firefox and was automatically redirected to my ISP hotspot's authentication webpage, entered my ID and password, and surfed). But when I rebooted, I couldn't connect to any network. So I switched back to network manager ...:(

Any thoughts ??

Thanks a lot,

AKoine

Below, the output of the recommended commands :

```
lspci -nn | grep "Broadcom Corporation"
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.
```

```
lsmod | grep "wl"
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl
```

```
sudo lshw -C network
[sudo] password for akoine: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:29:94:bb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.0.12 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0200000-f0203fff
```

---

