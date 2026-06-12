---
title: "iMac G5 wireless problem"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by Milad407 on 2009-12-23
Hi All

im new to ubuntu and i have a problem..
im dualbooting ubuntu 9.10 ppc and mac osx on My iMac G5 ppc non-iSight
its really great but i cant make the wireless work and the Bluetooth mouse and keyboard
im relly new at This forum so sorry if i posted in the wrong section

//Milad407

---

### Post by The Toxic Mite on 2009-12-23
Hello, and welcome to Ubuntu!

Go to Applications -> Accessories -> Terminal, and type in the following:

```

sudo lshw -c network
lspci -v less
iwconfig

```

Post the outputs here when done. Remember to put them in ```
 tags like this:

[noparse][code]
$ terminal output goes here

```[/noparse]

Thanks! :)

---

### Post by Milad407 on 2009-12-23
Hi thanks for your reply ! here is the code 
```

sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: Shasta (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@0001:03:0f.0
       logical name: eth0
       version: 00
       serial: 00:0d:93:7b:33:94
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sungem driverversion=0.98 duplex=half latency=16 link=no maxlatency=64 mingnt=64 multicast=yes port=MII speed=10MB/s
       resources: irq:40 memory:80400000-805fffff memory:80200000-802fffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0001:01:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=16
       resources: irq:60 memory:80084000-80085fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:24:bb:ef:2a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
milad@milad-desktop:~$ lspci -v less
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
-F <file>    Read PCI configuration dump from a given file
milad@milad-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

milad@milad-desktop:~$ 

```

---

