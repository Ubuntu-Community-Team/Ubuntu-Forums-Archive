---
title: "Dell wireless halts while on battery"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by patch1954 on 2011-06-11
Have a Dell Inspiron laptop with Ubuntu 10.04 and wireless card was up and running while on battery power when wireless card became disabled.   The wireless was running just fine and quit:

My iwconfig for wlan0:

sudo iwconfig wlan0
[sudo] password for XXXXX: 
wlan0     IEEE 802.11bgn  ESSID:"xxxxxxxxxx"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

and more diagnostics:
sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:12:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c7:fa:21:b0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:31 memory:fbd00000-fbd01fff

What do I need to do to stop the wireless from being turned off?

---

