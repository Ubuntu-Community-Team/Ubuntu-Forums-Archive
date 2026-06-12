---
title: "Dell laptop with Ubuntu 10.04: First no WiFi - Now no wired internet either!"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by bnegin on 2010-10-12
**Back story: **I have a Dell 600m laptop with a Broadcom wireless card - model BCM43xx. I installed Ubuntu on it in 2008. After installing some extra drivers for the Broadcom the WiFi was up and running. I put the computer away for a couple years because the screen was acting up (fuzzy and horizontal/vertical lines).

Fast forward a couple years and I just pulled the laptop out of my drawer. The screen suddenly is working fine. Bad news is, suddenly the Wifi stopped working. 

**Current problem: **I upgraded 10.04 but that didn't get the Wifi to work even after I used System>Administration>Hradware Drivers to update the driver got the green light to go on that indicates the driver is running and activated. At that point the wired internet was working. Today when I plugged in the ethernet cable I have no internet. There is a red exclamation mark over the network signal on top of the desktop and when I click on the network signal it says "No network devices available."

**Other notes:** Sometimes on startup I get a message that the power source is "unknown". No new software has been installed besides some games. I am a total Ubuntu newbie. 

Thanks in advance to you all!

---

### Post by dineshs on 2010-10-13
please post the results of the following terminal(applications-accessories-terminal)commands with ethernet cable plugged in```
sudo lshw -C network
```and```
iwconfig
```

---

### Post by bnegin on 2010-10-13
Thank you for the response!

Here are the results: 

boruch@boruch-laptop:~$ sudo lshw -C network
[sudo] password for boruch: 
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:faffe000-faffffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=32
       resources: memory:faffc000-faffdfff
boruch@boruch-laptop:~$ iwconfig
lo        no wireless extensions.

boruch@boruch-laptop:~$

---

