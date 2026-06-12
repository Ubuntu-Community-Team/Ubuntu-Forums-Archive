---
title: "no network connections using ubuntu 11.04(natty)"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by ScousaJAY on 2011-07-08
hi all, im a newbie to Ubuntu

i've installed ubuntu 11.04 on a friends Asus Eee pc 1005HA netbook. after the installation i tried to connect to the router using wireless, and when i enter the key, it fails to connect, so i tried using an Ethernet cable to connect but that doesn't work either, 

the network devices on the computer are:

Atheros AR8132 PCI-e fast ethernet controller
Atheros AR 9285 wireless network adapter

ive seen this thread posted here on the Ubuntu forums:  
[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

It lists the wireless device and the solutions to the problem, however, the solutions seem to be for Ubuntu 10.04 and also 10.10, and im not sure if it will work for 11.04

so far i have been unable to find out anything on the forums about the ethernet

can anyone point me in the right direction :)

thanks for the help

---

### Post by ScousaJAY on 2011-07-08
anyone got any ideas?

thanks

---

### Post by Iowan on 2011-07-08
While connected via the wired connection, from a terminal (Applications>Accessories>Terminal) check **ifconfig -a** to see if the interface gets an IP address. You might also check (and post, if possible) results of **sudo lshw -C network**

---

### Post by ScousaJAY on 2011-07-08
thanks for your reply Iowan, ive checked to see if it is assigned an IP address, and the results show it is not. below is the results from the second command:
 
```
[sudo] password for steve:
*-network 
description: Wireless interface
product: AR9285 Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
logical name: wlan0
version: 01
serial: 00:25:d3:ca:6e:d9
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath9k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
resources: irq:17 memory:fbff0000-fbffffff
*-network[
description: Ethernet interface
product: AR8132 Fast Ethernet
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:01:00.0[
logical name: eth0
version: c0
serial: 90:e6:ba:6c:a2:5a
size: 100Mbit/s
capacity: 100Mbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
```
 
 
again, thanks for your time

---

### Post by ScousaJAY on 2011-07-09
just a quick update, 
i have got the wireless going with no problems. i logged into the router  using windows and looked at assigned IP addresses for wireless devices  and found two entry's for the onboard wireless device , one named after  my user account in windows, and one called Ubuntu, both of which at this  point "not connected". i deleted the Ubuntu entry from the list, logged  out of the router page, restarted the computer and booted into Ubuntu.  it connected automatically and is working fine, 

still no closer to finding the solution to the ethernet though :smile:

just for reference the router i have is a BT home Hub version 2.0..(UK)

if anyone runs into problems logging into this router and recieves an error stating "only 100 sessions allowed, please wait for a session to expire".    do the following:


[LIST]
[*]disconnect your device's from the router
[*]turn the router off for 30 seconds
[*]turn the router back on, reconnect your devices & attempt to login to the router again and it should work
[/LIST]

---

### Post by ScousaJAY on 2011-07-10
anyone know of anything i can try to get the wired connection going

i found a thread by another user who uses the same netbook (Asus 1005HA) and i think he has the same problem as me.

here is his thread:

[http://ubuntuforums.org/showthread.php?t=1801298](http://ubuntuforums.org/showthread.php?t=1801298)

thanks for any help :):)

---

### Post by chili555 on 2011-07-10
> *-network
description: Ethernet interface
product: AR8132 Fast Ethernet
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:01:00.0
logical name: [COLOR="Red"]eth0[/COLOR]
version: c0
serial: 90:e6:ba:6c:a2:5a
size: 100Mbit/s
capacity: 100Mbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes [COLOR="Red"]driver=atl1c [/COLOR]driverversion=1.0.1.0-NAPI duplex=full firmware=N/A latency=0 [COLOR="Red"]link=yes[/COLOR] multicast=yes port=twisted pair [COLOR="Red"]speed=100Mbit/s[/COLOR]
resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=12Wow! I don't see anything to dislike. Please reboot and then click the Network Manager icon. Does it show a wired network as available? Please run and post:```
dmesg | grep -e **atl** -e eth0
```The highlighted part is lower case ATL, not ATone. Thanks.

---

### Post by ScousaJAY on 2011-07-11
hi chili, thanks for the reply, heres the result of the command you asked me to run:

dmesg  |  grep -e atl -e eth0
[    1.381473] atl1c 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.381504] atl1c 0000:01:00.0: setting latency timer to 64
[    1.513956] atl1c 0000:01:00.0: version 1.0.1.0-NAPI
[   20.976303] atl1c 0000:01:00.0: irq 45 for MSI/MSI-X
[   21.037219] ADDRCONF(NETDEV_UP): eth0: link is not ready


when i click the network icon, i get the following options:

wired network (blanked out)
diconnected   (blanked out)
wireless network (blanked out)  seems to work fine and connects fully

when it try connecting using the ethernet cable, it shows that it is connecting and then after about 30 seconds it says disconnected

thanks chili :)

---

### Post by chili555 on 2011-07-11
> when it try clicking on auto eth0 it says connecting and then after about 30 seconds it says disconnectedI'd like to try to capture a syslog entry showing the attempt and failure to connect. Try to connect and let it fail and then do:```
sudo cat /var/log/syslog | grep -e atl1 -e ethwork | tail -n20 > SJay.txt
```Copy and paste from the text file in your reply. Thanks.

---

### Post by ScousaJAY on 2011-07-12
i have just tried running that command but i cant seem to find the log file, where would i locate it?

thanks :)

---

### Post by chili555 on 2011-07-12
In your user directory.

---

