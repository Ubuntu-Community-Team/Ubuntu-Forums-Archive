---
title: "Blitzz Wireless Card dropping connection"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by Diamond B on 2009-04-04
I'm a newbie, escaping the Microsoft tentacles and I recently installed Ubuntu 8.10 on my laptop.  I have a Blitzz Wireless card that will connect to my wireless network when I boot up, but the connection will only last 5 minutes, if I'm lucky.  After it disconnects, I cannot get it to reconnect and I'm at a complete loss as to what is up.  Any help would be appreciated, as I don't want to go out and buy a new card.

Here's the information on my system:
Dell Inspiron 8200

Wireless Card Info
07:00.0 Network controller: ADMtek ADM8211 802.11b Wireless Interface (rev 11)


Interface
wmaster0  no wireless extensions.



wlan0     IEEE 802.11b  ESSID:""  

          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   

          Tx-Power=27 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Modules
adm8211                32512  0 

mac80211              216820  1 adm8211

eeprom_93cx6           10240  1 adm8211

cfg80211               32392  2 adm8211,mac80211


Boot Messages
[   23.351310] adm8211 0000:07:00.0: enabling device (0000 -> 0003)

[   23.351332] adm8211 0000:07:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11

[   23.351356] adm8211 0000:07:00.0: setting latency timer to 64


Network Configuration
 *-network

       description: Wireless interface

       product: ADM8211 802.11b Wireless Interface

       vendor: ADMtek

       physical id: 1

       bus info: pci@0000:07:00.0

       logical name: wmaster0

       version: 11

       serial: 00:e0:98:a3:64:3c

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=adm8211 latency=64 maxlatency=128 mingnt=64 module=adm8211 multicast=yes wireless=IEEE 802.11b

  *-network DISABLED

       description: Ethernet interface

       physical id: 3

       logical name: pan0

       serial: 9e:62:9f:13:d9:bb

       capabilities: ethernet physical

       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Version
Ubuntu 8.10

Kernel/Architecture
2.6.27-11-generic i686

---

