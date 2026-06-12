---
title: "[Atheros 9285/Ubuntu 12.04/Cybele all in one"
date: 2012-12-14
forum: Networking &amp; Wireless
---

### Post by olivierchapron on 2012-12-14
Hello
I cannot reach my wifi because the card is not active.
My all in one has no button to switch on the wifi (only tactile one no available).
Have you any idea ?

 Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        74:2F:68:B4:0C:9A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 74:2f:68:b4:0c:9a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-29-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f7400000-f740ffff

---

