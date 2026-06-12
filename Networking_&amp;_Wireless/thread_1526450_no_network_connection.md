---
title: "no network connection"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by 562sparky562 on 2010-07-08
hello,

New to ubuntu, my wired and wireless connection doesn't work.

Please help

---

### Post by Gregorybekkers on 2010-07-08
If you (right) click on the network icon in you pannel you can Enable or Disable Network Connections.

---

### Post by pedro_orange on 2010-07-08
Hello. 

If you wish to receive help on this issue I'm afraid we're going to need some additional information regarding your network configuration and system specifications, such as:

- NIC vendor
- Can the machine see your network devices? (lspci -C network)
- What does the output of ifconfig say?
- Do you have an IP Address?

You may also wish to consult the online documentation located at: [https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)

---

### Post by tarps87 on 2010-07-08
> **pedro_orange said:**
> Hello. 

If you wish to receive help on this issue I'm afraid we're going to need some additional information regarding your network configuration and system specifications, such as:

- NIC vendor
- Can the machine see your network devices? (lspci -C network)
- What does the output of ifconfig say?
- Do you have an IP Address?

You may also wish to consult the online documentation located at: [https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)

Just to expand the two commands that are required are to be entered into the terminal, they are:
```
lspci -C network
```
and
```
ifconfig
```
As mention above

---

### Post by 562sparky562 on 2010-07-08
if i enter the ip addres, net mask and dns address manually it shows i'm connected but i still can't go online. 
 
here's the output of the commands
 
elsa@elsa-laptop:~$ lspci -C network
lspci: invalid option -- 'C'
Usage: lspci [<switches>]
Basic display modes:
-mm Produce machine-readable output (single -m for an obsolete format)
-t Show bus tree
Display options:
-v Be verbose (-vv for very verbose)
-k Show kernel drivers handling each device
-x Show hex-dump of the standard part of the config space
-xxx Show hex-dump of the whole config space (dangerous; root only)
-xxxx Show hex-dump of the 4096-byte extended config space (root only)
-b Bus-centric view (addresses and IRQ's as seen by the bus)
-D Always show domain numbers
Resolving of device ID's to names:
-n Show numeric ID's
-nn Show both textual and numeric ID's (names & numbers)
-q Query the PCI ID database for unknown ID's via DNS
-qq As above, but re-query locally cached entries
-Q Query the PCI ID database for all ID's via DNS
Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]] Show only devices in selected slots
-d [<vendor>]:[<device>] Show only devices with specified ID's
Other options:
-i <file> Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file> Look up kernel modules in a given file instead of default modules.pcimap
-M Enable `bus mapping' mode (dangerous; root only)
PCI access options:
-A <method> Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val> Set PCI access parameter (see `-O help' for a list)
-G Enable PCI access debugging
-H <mode> Use direct hardware access (<mode> = 1 or 2)
-F <file> Read PCI configuration dump from a given file
 
elsa@elsa-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1b:24:35:83:eb 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:16 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:72 errors:0 dropped:0 overruns:0 frame:0
TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:5600 (5.6 KB) TX bytes:5600 (5.6 KB)
wlan0 Link encap:Ethernet HWaddr 00:19:7e:56:00:80 
inet6 addr: fe80::219:7eff:fe56:80/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:12 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:3900 (3.9 KB) TX bytes:2736 (2.7 KB)
[EMAIL="elsa@elsa-laptop:~$"]elsa@elsa-laptop:~$[/EMAIL] 
 
I've googled and searched for info and I couldn't figure it out.
 
thanks for your help

---

### Post by tarps87 on 2010-07-08
Sorry just copied the commands and didn't check them.
```
lshw -C network
```

Have you any other devices connected to the network?

---

### Post by 562sparky562 on 2010-07-08
hello tarps87,
 
elsa@elsa-laptop:~$ sudo lshw -C network
*-network 
description: Ethernet interface
product: 88E8038 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 14
serial: 00:1b:24:35:83:eb
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
resources: irq:27 memory:24000000-24003fff ioport:2000(size=256)
*-network
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 01
serial: 00:19:7e:56:00:80
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:17 memory:24400000-2440ffff
[EMAIL="elsa@elsa-laptop:~$"]elsa@elsa-laptop:~$[/EMAIL] 
 
 
there is nothing else connected.
 
i am using a cable modem directly connected to my desktop.
 
I switch the cable to the laptop when i wanna try to connect to the internet
from the laptop.  i have the same settings on the laptop but i can't access the 
internet from the laptop.
 
The only difference i see when i check the connection information from the desktop
and the laptop is that the laptop doesn't show a default route while the desktop does.
 
Thanks again for your help =)

---

### Post by Iowan on 2010-07-08
> **562sparky562 said:**
> 
i am using a cable modem directly connected to my desktop.
 
I switch the cable to the laptop when i wanna try to connect to the internet
from the laptop. It might be necessary to reset (power cycle) the modem. Some of them "lock onto" a MAC address.

---

### Post by 562sparky562 on 2010-07-08
ok i'll try that.
 
thanks iowan =)

---

### Post by 562sparky562 on 2010-07-08
no that didnt work  thanks anyway, iowan.

---

### Post by Iowan on 2010-07-08
> **562sparky562 said:**
> if i enter the ip addres, net mask and dns address manually it shows i'm connected but i still can't go online. 
 Are you entering the manual information into Network Manager, or directly into */etc/network/interfaces*?

---

### Post by 562sparky562 on 2010-07-09
into network manager

---

### Post by tarps87 on 2010-07-09
Just a though when you enter the details manually I assume you use the desktop pc's details as a reference. If you do this and check the subnet and gateway are the same and the ip patten matches try pinging the modem

---

### Post by 562sparky562 on 2010-07-09
I pinged the router and that's a screenshot of the result.
 
I assume that means the network card is working right?
 
I appreciate the help you guys. =)

---

### Post by tarps87 on 2010-07-09
You are correct, it is working and you can connect to the modem, the issue appears to be passing through the router. I am assuming pinging google does not work? Could you post the current ip settings, specifically the gateway.

It's no problem

---

### Post by 562sparky562 on 2010-07-09
the first screenshot is from my laptop running ubuntu 10.04 lts.
 
the second one is from my working desktop which is running windows vista
and ubuntu 10.04lts and i can connect to the internet from both OS's.
 
notice that the laptop does not show a default route/gateway.

---

### Post by tarps87 on 2010-07-09
You appear to be missing the default route setting, try setting the gateway setting in the networkmanger (IPv4) to 76.175.48.1 then disconnect and reconnect

---

### Post by 562sparky562 on 2010-07-09
My wired network is now working.

Thank you Tarps87, iowan, pedro_orange, and gregorybeckers.

You guys rock =)

Tarps i did what u suggested and it worked.  I then changed the settings in network manager
to automatic dhcp and restarted the cable modem and laptop twice and it's working perfect now.

Thanks again everyone =)

---

### Post by tarps87 on 2010-07-09
I wonder why dhcp didn't work before, anyway glad it's working

---

