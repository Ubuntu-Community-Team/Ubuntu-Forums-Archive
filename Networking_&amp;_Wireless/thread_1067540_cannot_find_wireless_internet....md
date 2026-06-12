---
title: "cannot find wireless internet..."
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by philgift on 2009-02-12
please help me for i am new to the world of linux and somewhat to wireless internet in general. i also have searched the forum for approximately one hour with no results. the answers that i have found seem to be specific to certain hardware or setups...

the situation:

on the main computer (running winXP), the broadband router is connected to. i do not have access to this computer as it is used by someone else through their company, HOWEVER, i do have the name, password, etc... the router itself is a "linksys wireless-G model: WRT54G" and my computer has a pci wireless card as well: "linksys wireless-g model: WMP54GS".

now, this all worked perfectly when running winxp on my computer. but after making the switch to ubuntu (i wanted to educate myself in the ways of linux while taking advantage of open source and free software and blah blah blah), i find that i have no idea how to find the network itself. it is a wpa-enabled network and after typing in what i think is the correct info into the network manager, nothing happens still.

please help me. i'm sure that something is just misconfigured and i REALLy want to learn how to make this work. i will give out whatever other info i need to. i just want to be able to use my internet again :(

thank you.

---

### Post by superprash2003 on 2009-02-12
we first need to see if ubuntu recognized your linksys.. post output of the following commands from the terminal ( copy paste method)
1)lshw -C network
2)iwconfig
3)iwlist scanning

---

### Post by philgift on 2009-02-12
(lshw -C network)

  *-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:b6:57:ab:8f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 72:e6:50:63:25:ab
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


(iwconfig)

lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


(iwlist scanning)

lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

and there ya go. hopefully we can get this to work...

---

### Post by superprash2003 on 2009-02-14
hmm..wlan0 says no scan results which mean it didnt find any wifi networks around.. are you sure you have wifi networks around?? if so, you could try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

