---
title: "Accessing a Windows XP network."
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by Pale Chapter on 2009-07-29
I'm currently vacationing with my grandparents, and I can't access the household wireless network with my laptop--I had to connect directly to the router with an ethernet cable (so... *primitive*!) to write this. Any tips?

---

### Post by j7%&lt;RmUg on 2009-07-29
Does the network have a WPA key? if so you will have to enter that key to access the network.

Let me know what happens.

---

### Post by Pale Chapter on 2009-07-29
It has a WEP key, and when I enter it in its entirety nothing happens; it just asks for authentication again. I can't even detect the network; it seems to be hidden.

---

### Post by Pale Chapter on 2009-07-31
Bumping; this is really inconvenient for everybody in the house, and I have no clue what to do. Could really,* really* use some help or advice here.

---

### Post by dmizer on 2009-07-31
Try rebooting the router. Seems silly, but it could work. Also, please post the output of:
```
lshw -C network
```

---

### Post by Pale Chapter on 2009-08-02
No luck--and that line of code produced this:
```
lspci: invalid option -- 'C'
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file

```

---

### Post by dmizer on 2009-08-03
Argh ... sorry. I gave you the wrong command. Try this instead:
```
lshw -C network
```

---

### Post by Pale Chapter on 2009-08-04
Thanks!
```
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:7e:92:d0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:24:6f:d8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.101 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9a:cc:c6:21:71:fd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by dmizer on 2009-08-04
Try this: [http://ubuntuforums.org/showpost.php?p=7305030&postcount=12](http://ubuntuforums.org/showpost.php?p=7305030&postcount=12)

---

### Post by Pale Chapter on 2009-08-04
I appear to have lost all wireless capability. This isn't really a big problem right now, since the current network connection is physical, but I go home to my own network (and my college's wi-fi! O.o) tomorrow.```
jonathan@jonathan-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
jonathan@jonathan-laptop:~$ sudo iwlist scan
[sudo] password for jonathan: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

jonathan@jonathan-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
jonathan@jonathan-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

jonathan@jonathan-laptop:~$ uname -rm
2.6.28-14-generic x86_64
jonathan@jonathan-laptop:~$ dmesg | grep -e ndis -e wlan
[   11.350711] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   11.410503] usbcore: registered new interface driver ndiswrapper
jonathan@jonathan-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:24:6f:d8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.101 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:80:96:35:91:e2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
jonathan@jonathan-laptop:~$ clear

jonathan@jonathan-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
jonathan@jonathan-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

jonathan@jonathan-laptop:~$ uname -rm
2.6.28-14-generic x86_64
jonathan@jonathan-laptop:~$ dmesg | grep -e ndis -e wlan
[   11.350711] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   11.410503] usbcore: registered new interface driver ndiswrapper
jonathan@jonathan-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:24:6f:d8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.101 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:80:96:35:91:e2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
jonathan@jonathan-laptop:~$ 
jonathan@jonathan-laptop:~$ clear

jonathan@jonathan-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
jonathan@jonathan-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

jonathan@jonathan-laptop:~$ uname -rm
2.6.28-14-generic x86_64
jonathan@jonathan-laptop:~$ dmesg | grep -e ndis -e wlan
[   11.350711] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   11.410503] usbcore: registered new interface driver ndiswrapper
jonathan@jonathan-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:24:6f:d8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.101 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 06:80:96:35:91:e2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by dmizer on 2009-08-04
Well, you can just uninstall Ndiswrapper, and remove the following lines from /etc/modprobe.d/blacklist.conf
```
blacklist wl
blacklist b43
```
(it's a long file, but those two lines will be at the very bottom.)
Then reboot, and you'll be right back where you started.

---

### Post by Pale Chapter on 2009-08-05
Done--now I've got until December to figure this out before we're back up here.

---

