---
title: "Atheros AR928X Wireless Adapter connected, on but &quot;disabled&quot; Ubuntu 9.04 Acer Extensa"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by eahl4 on 2009-04-24
I am using an Acer Extensa 4630Z, dual-partitioned for Ubuntu 9.04 and Windows Vista.  My wireless card works fine in Vista, and in Ubuntu it shows up as "active" under my wireless networks, but the internet does not seem to be connected.  I am very new to Ubuntu-- the wired connection works wonderfully, but I wondered if someone could help me get the wireless to work too.  I have tried several solutions from other forum posts without success.

A few solutions I tried unsucessfully have been:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=968653](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=968653)
[http://ubuntuforums.org/archive/index.php/t-963791.html](http://ubuntuforums.org/archive/index.php/t-963791.html)
(and keep in mind I know nothing--very much a newbie)

Thank you in advance for your help!

when I type:

sudo lshw -C network 

in a terminal, I get this:

  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4d:3f:21:99
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.160 latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:cc:5b:ae
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5764m-v3.35 ip=192.168.0.167 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e6:44:37:5f:b9:3e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by eahl4 on 2009-04-25
I followed Volanin's instructions at:[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097), post #5 and now I get the following response to iwconfig--does "Rx invalid nwid:0" mean anything?:

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"friedline"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:6B:29:9F:86   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=95/100  Signal level:-55 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by SuperNoa on 2009-04-29
I have the same problem on a DELL Studio XPS 13" with Ubuntu 9.04 64bit and Atheros AR928X Wireless Network Adapter! 
I have solved installing linux-backports-modules-jaunty-generic!

---

### Post by lyth on 2009-07-21
i have the same problem with my acer aspire 5737z and i have the same wireless card as you (AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

