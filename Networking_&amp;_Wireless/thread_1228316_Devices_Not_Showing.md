---
title: "Devices Not Showing"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by tecknomage on 2009-07-31
First, from other posts I figure I would provide this:

        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
           *-network DISABLED
                description: Wireless interface
                product: Wireless WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 00
                serial: 00:22:fa:2d:2c:e4
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

tecknode@ubuntu:~$ dmesg | grep -e ath -e wlan
[    3.821345] device-mapper: multipath: version 1.0.5 loaded
[    3.821348] device-mapper: multipath round-robin: version 1.0.0 loaded

tecknode@ubuntu:~$ uname -rm
2.6.28-14-generic i686

tecknode@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

-------------------------------------------------------------

Wireshark does NOT list wlan0.

WPA GUI does NOT show any Adapters nor Networks.

What's going on? How do I get both apps to see what I have?

---

