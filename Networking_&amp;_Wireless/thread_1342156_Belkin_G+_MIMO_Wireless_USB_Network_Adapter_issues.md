---
title: "Belkin G+ MIMO Wireless USB Network Adapter issues"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by joejoy on 2009-11-30
Hi All:

I am new to setting up Ubuntu with wireless network adapter. Recently I bought a Belkin G+ MIMO Wireless USB Network Adapter F5D9050 Ver 4000. I was able to connect to my home wireless network pretty much out of the box. However I can get signal strength max only up to 70%. I dont have this issue with windows XP.


I did not install any drivers. So I am thinking the issue may be it is using some default driver and updating the driver may help. 

Question I have is how to find out which driver is being currently used? And does any know a fix to this issues. Since my network adapter is sitting next to my router I am assuming It should have signal strength more the 90%

Here is some of my other info

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 8086:0110 Intel Corp. Easy PC Camera
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:905c Belkin Components Wireless G Plus MIMO Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Any help is appreciated.
Thanks,

---

### Post by joejoy on 2009-11-30
here is some more info

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562V 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:65:0b:8b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 latency=0 module=e1000e multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:26:9a:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.3.102 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:a5:7f:af:dd:f5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by joejoy on 2009-11-30
some more info

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"MAIN-HOME"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:23:43:4F   
          Bit Rate=11 Mb/s   Tx-Power=12 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=63/100  Signal level:-16 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

