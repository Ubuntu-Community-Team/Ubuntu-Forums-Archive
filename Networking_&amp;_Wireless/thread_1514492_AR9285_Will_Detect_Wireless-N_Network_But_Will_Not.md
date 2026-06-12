---
title: "AR9285 Will Detect Wireless-N Network But Will Not Connect"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by stuff_happens on 2010-06-21
I have an AR9285 (Atheros) and it supports 802.11n. I setup my router so it was wireless-n only. Rebooted router and rebooted computer. Xubuntu loads up wireless fine, detects the network and tries to connect to it. It eventually times out trying to connect. If I put router back to wireless-g it connects fine. I have the following output:

```
stuff_happens@home:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Evil Chicken"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
stuff_happens@home:~$ sudo lshw -C network
[sudo] password for stuff_happens: 
PCI (sysfs)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: XX:XX:XX:XX:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.32-23-generic firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:fbef0000-fbefffff
```

Its using ath9k which has support for 802.11n, and it looks like it works since it can detect the network, but connecting is the problem. Btw it uses WPA2, which works fine under 802.11g. Any help greatly appreciated =o)

---

### Post by stuff_happens on 2010-06-21
Any ideas anyone on what could be the problem?

---

### Post by stuff_happens on 2010-06-25
=o( help? please.

---

### Post by nickmcg on 2010-06-29
If you're using karmic, you may need to use the backports.

Lucid, I'm not sure - I get a connection, but unrecognised speed which seems to fluctuate (iwconfig reports 'Bit Rate=0 kb/s').

Search the forums for 'atheros 928x' and take your pick - good luck. Please post if you find something that works.

Update:
Under Lucid, installed 'linux-backports-modules-wireless-lucid-generic', shows 150 Mb/s throughput, much more consistent signal strength.

Cheers

Nick

---

### Post by stuff_happens on 2010-06-29
I had already install all the backports for Lucid and still it was detecting the network but not connecting. The network icon for network-manager was showing only one turning green so it wasnt even communicating with the router. In "G" its the opposite. I'll check out the other posts and see what I can try as well. Btw is there any specific settings I need to do for "N" on router so that it works? Not sure if the wireless drivers support everything for "N" yet.

---

### Post by nickmcg on 2010-06-29
Some routers can be funny about mixed n/g networks.

Have you tried using wicd instead of network manager - some threads imply that network manager may be [part of] the problem.

Cheers

Nick

---

### Post by stuff_happens on 2010-06-29
I setup router so its N only. I'll check out wicd and see how it goes. I tried solutions in the other threads regarding my card and still no success. Thanks for the replies. =o)

---

