---
title: "Kismet conf source package error"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by Searay on 2009-02-22
Having trouble configuring the source line. I get this error

Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Illegal card source line 'wlan0, rt2500'
Done.

I am using a WUSB54g ver 4, not sure if I need help installing a driver?

 lshw -C network
  *-network               
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 11
       serial: 00:04:5a:89:71:c0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.2.16 latency=64 maxlatency=128 mingnt=64 module=tulip multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:c1:41:cc:17:36
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:bf:74:a1:18
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.106 multicast=yes wireless=IEEE 802.11bg


and finally 

Sources are defined as:
# source=rt2500-gpl,wlan0
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=wlan0, rt2500

---

### Post by Searay on 2009-03-02
Are there any resources I can look to for some support?

---

### Post by Searay on 2009-03-08
Answer: 
source=rt2500,wlan0,WUSB54G
this worked

---

