---
title: "kismet configuration - not working"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by udippel on 2012-06-22
There is this fantastic, but closed, thread:
[http://ubuntuforums.org/showthread.php?t=1067390](http://ubuntuforums.org/showthread.php?t=1067390)

I followed it, though can't succeed.
Here is what I get:

> Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ath9k' in source 'ath9k,wlan0,piran'
Done.

I have changed the conf-file as suggested:

>   *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: f0:7b:cb:6e:f2:34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-25-generic firmware=N/A ip=192.168.116.41 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f0100000-f010ffff

So I was sure to have the correct driver, ath9k

And I also use the right interface (I hope):

> lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"piran"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:F5:22:24:40   
          Bit Rate=24 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1296  Invalid misc:849   Missed beacon:0

eth0      no wireless extensions.


What is wrong here?

---

