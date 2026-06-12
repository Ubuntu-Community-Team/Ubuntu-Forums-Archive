---
title: "New install can't access Internet on work wireless"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by SkullOne on 2012-02-24
Greetings,

I'm having a bit of trouble getting my laptop to connect to the Internet via the public WiFi (WPA2 secured) we have at work.  It works just fine at home on my WiFi (WPA2 secured).  

I'm now using 64-bit Kubuntu 11.10.  I just left 64-bit Xubuntu 11.10 which likewise had the issue with my works wireless which helped me decide to wipe and start new (other then being bored with XFCE and I won't touch Unity) because I figured maybe I screwed something up back in December when I loaded Xubuntu and toyed around with everything.

I can connect to the wireless, but I can't get to the Internet.  I can see the network and browse whatever shares are there, but the Internet is a no go. Windows laptops connect just fine to the wireless and work correctly.  Android phones do the same as well.

Thanks in advance!

1) Samsung AMD A6 Laptop with 8GB RAM running Kubuntu 11.10 with Kernel 3.0.0-12 - latest Catalyst drivers have been loaded to get around the nomodeset in GRUB.  This is a base 11.10 install.  No updates yet.  This install hasn't even touched my home network yet.

2) Atheros AR9485 Wireless Network Adapter

3) wlan0     IEEE 802.11bgn  ESSID:"pi-guest"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:09:0F:E8:A9:C9   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:16  Invalid misc:537   Missed beacon:0

4) jason@jason-dev:~$ lsmod | grep "ath9k"
ath9k                 127538  0 
mac80211              310872  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312866  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath

5) jason@jason-dev:~$ dmesg | grep "ath9k"
[    6.672436] ath9k 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.672454] ath9k 0000:04:00.0: setting latency timer to 64
[    6.700397] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[    6.701540] Registered led device: ath9k-phy0

6) *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: e8:11:32:e5:ed:bf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=192.168.111.115 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fea00000-fea7ffff memory:fea80000-fea8ffff

7) jason@jason-dev:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.111.5   0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.111.0   0.0.0.0         255.255.255.0   U     2      0        0 wlan0

---

