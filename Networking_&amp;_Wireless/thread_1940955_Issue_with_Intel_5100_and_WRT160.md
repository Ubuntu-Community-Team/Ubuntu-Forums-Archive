---
title: "Issue with Intel 5100 and WRT160"
date: 2012-03-14
forum: Networking &amp; Wireless
---

### Post by k0d3k on 2012-03-14
I am having issues with my wireless setup.  I have run the following commands:
lshw -c Network
 *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:dc:06:ac
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-16-generic-pae firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:ff900000-ff901fff

rfkill list
0: Toshiba Bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no                                                                                                                                                            
2: hci0: Bluetooth                                                                                                                                                                  
        Soft blocked: no                                                                                                                                                         
        Hard blocked: no 

The option to save my configuration is grayed out.  I tried to see if I could blacklist a module but I don't have the modules listed in order to do so.

Any idea as to what is going on?

---

### Post by k0d3k on 2012-03-16
Fixed, I installed the latest 12.04 release from Daily Builds and works like a charm, strange how it didn't work in 11.10 even though that model of network card is supported according to the FAQ.

---

