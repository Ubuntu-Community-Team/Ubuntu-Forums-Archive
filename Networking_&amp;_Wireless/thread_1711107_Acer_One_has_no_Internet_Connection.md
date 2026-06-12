---
title: "Acer One has no Internet Connection"
date: 2011-03-20
forum: Networking &amp; Wireless
---

### Post by desert dweller on 2011-03-20
I have installed Ubuntu 10.04 from the CD that came with a book entitled "Ubuntu for Non-Geeks," and neither my wireless or wired internet connection is working. (I'm sending this request on another computer.)

I installed 10.04 on an Acer Aspire One AOD255E-13639 netbook. It has an Atheros Communications AR8152 V1.1 fast ethernet card and a Broadcom Corp Device 4727.

I found this thread in the forums that addresses the issue: [http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)

I downloaded the compat-wireless-2.6.tar.bz2 driver as suggested, but I couldn't get the terminal commands to work that were given for installing it. I kept getting errors. (I downloaded the tar file on a computer that has an internet connection and transferred it to the desktop of the Acer using a flash stick.)

Eventually, I double-clicked on the tar file and opened it with Archive Manager. I now have a folder on my desktop "compat-wireless-2011-03-20". Is there a way I can use this folder to install the driver?

I'm new to Ubuntu and haven't used the terminal commands before.

Thanks.

---

### Post by uncaspi on 2011-03-20
Click Applications(upper left panel)click Accessories and then look for the terminal or console.

---

### Post by desert dweller on 2011-03-21
Here's some additional info:

I typed "sudo lshw -C network" in the terminal and got this reply:

*-network UNCLAIMED     
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:97000000-9703ffff ioport:5000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:96000000-96003fff

---

### Post by uncaspi on 2011-03-21
None of the cards have driver loaded.
Will you please post the content of
sudo lspci grep network

---

### Post by desert dweller on 2011-03-21
Hi, Uncaspi --

Here's the output from sudo lspci grep network.

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

---

### Post by uncaspi on 2011-03-21
Sorry for applying wrong syntax. Try this

sudo lspci -nn

---

### Post by desert dweller on 2011-03-21
Here's the output from sudo lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)

---

### Post by uncaspi on 2011-03-21
your ethernet card is Atheros .Code 1969:2060 and wireless is
Broadcom code 14e4:4727

You can find the drivers by viewing the file
i.e this command
sudo grep 14e4 /lib/modules/`uname -r`/modules.pcimap grep 4727

the driver is listed leftmost. Then run
sudo modprobe <driver>
suddo depmod -a

When the drivers are loaded you shold be able to connect.

---

### Post by desert dweller on 2011-03-21
Unfortunately, my computer is having trouble with this command. It says:

grep: grep: No such file or directory
grep: 4727: No such file or directory

---

### Post by desert dweller on 2011-03-22
After trying several fixes, I also succeeded in breaking the Windows system that I had installed in a dual boot configuration with 10.04. So I decided to start from scratch, and installed 10.10 as the sole operating system. It worked immediately and I have both wireless and wired internet connections. The loss of the Windows system is no big deal because I had been planning to eliminate it as soon as I got Ubuntu working properly. Thanks for the help.

---

