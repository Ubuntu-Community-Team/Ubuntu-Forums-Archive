---
title: "wireless card"
date: 2006-02-14
forum: Networking &amp; Wireless
---

### Post by sly on 2006-02-14
I just installed ubuntu 5.10 on a dell laptop (used to run fedora). I have a D-Link wireless card dwl-g630. It gets detected, I can activate it and assign the ssid...
I see it with iwconfig & ifconfig, but it can't get an ip. dhclient returns: "No working leases in persistent database - sleeping."
Any suggestions? Thanx!
Do I have to install ndiswrapper like in fedora? But there my card wasn't even detected.

---

### Post by Lambert on 2006-02-14
Probalby not but more information is needed.

Post output of these commands

sudo lshw -C network
iwconfig


What kind of network settings are you using? Open or encrypted? if encrypted wep or wpa? if wep what kind of key hex or phrase? shared or open key?

there might be more questions but we can start here.

---

### Post by sly on 2006-02-14
sudo lshw -C network
 *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@03:00.0
       logical name: wlan0
       version: 00
       serial: 00:0f:3d:46:6c:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:20820000-20821fff iomemory:20800000-2081ffff irq:11

----------------------------
iwconfig
wlan0     IEEE 802.11b+/g+  ESSID:"SuTecK"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have no enc.

---

### Post by Lambert on 2006-02-14
first I suggest looking [here]("http://doc.gwos.org/index.php/ACXDriver") and trying the part in breezy about the firmware. If that doesn't work see this link and read through.


[http://www.houseofcraig.net/acx100_howto.php]("http://www.houseofcraig.net/acx100_howto.php")

Also somebody else with more experience with this chipset is going to have to chime in.

You already have the driver installed so ignore the compile part of the howto. I believe you just need the firmware part and other configurations explained in the link. But I have no experience setting up this chipset.

---

### Post by sly on 2006-02-17
thanx Lambert! the new firmware worked perfect. 
i appreciate it!

---

