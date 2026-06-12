---
title: "Broadcom BCM 4313 sees AP but doesn't connect"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by moehabibi on 2011-03-24
Good Morning, after-noon, and night. =]

My wireless BCM 4313 b/g/n on a FRESH install of UBUNTU 10.10 isn't working properly. As I " Enable Wireless " it stays for about a minute to find my AP, once it finds my AP I double click my AP and enter my password (WPA2-Personal)and it starts to connect. It then, after about 15-30 sec it asks me for my password once again simply by the same window(like as if I'm connecting to it for the first time) with out any error message. 

There are many posts for the BCM 4313 regarding it not working, but mine is WORKING, but simply being weird and not connecting.


I have googled but like i said they seem to be trying to fix the fact that it is not working completely.

Laptop - Toshiba Satellite A660 
Ubuntu 10.10 UPTODATE
1.6 i7
4GB
nVidia 330M  


if you guys need anything else please ask and i will provide as i dont know what else to give info on

---

### Post by david.flights on 2011-03-24
Hello- I am experiencing identical symptoms to your problem. I am running Ubuntu Netbook Remix 10.10 with a Asus eeepc 1015PE. My problem is I cannot connect to any wireless networks. Wired network works fine.

Machine: Asus eeePC 1015PE
Wirelss: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
Ubuntu: 10.10 
Kernel: 2.6.35-22-generic i686


I have tried to download the BM4313 drivers from thier website, but can't follow the install instructions correctly.

I have checked the BIOS for onboard devices and both WLAN and LAN are enabled.

I have run sudo apt-get update while connected to the wired network. 
I have tried (unsucesfully):
sudo apt-get install linux-backports-modules-jaunty 
sudo apt-get install linux-backports-modules-wireless-lucid-generic 
sudo apt-get install linux-backports-modules-intrepid-generic
sudo apt-get install cabextract
sudo apt-get install ndisgtk
sudo apt-get install ndiswrapper-utils-1.9

sudo apt-get install b43-fwcutter

---

### Post by josephmills on 2011-03-24
if you have it (wlan0) in ifconfig then the driver is there have you tried to
```
sudo apt-get update 
```
```
sudo apt-get upgrade 
```
```
sudo reboot 
```
also could you post 
```
lspci grep|14e4 
```

---

### Post by david.flights on 2011-03-25
I have tried sudo apt-get update many times during this process. 

Below is my output from  lspci grep|14e4
[/B]Usage: lspci [<switches>]

Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file

---

### Post by ioane on 2011-05-16
> **moehabibi said:**
> 

There are many posts for the BCM 4313 regarding it not working, but mine is WORKING, but simply being weird and not connecting.


I have the same wireless card and I just found out that it will not go faster than 65Mbps (some say 72Mbps but mine connects very shortly on 72 and falls back at 65). The reason for this symptom could be that you have your AP on wireless N-only higher than 65Mbps.

[http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4313](http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4313)

---

