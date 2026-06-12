---
title: "Elitebook 8560P &amp; Intel 6000 Wifi Prob"
date: 2012-01-11
forum: Networking &amp; Wireless
---

### Post by JackNBox on 2012-01-11
I have an HP Elitebook 8560P running Ubuntu 10.10 Maverick Meekat that I am trying to get Wireless to work on.  Below is some relevant information.
Anyone have any ideas what my problem can be?

uname -a
Linux ACLan03 2.6.35-31-generic-pae #63-Ubuntu SMP Mon Nov 28 20:48:50 UTC 2011 i686 GNU/Linux


iwconfig (note I do not see a wlan0)
lo        no wireless extensions.
eth0      no wireless extensions.
vboxnet0  no wireless extensions.

lshw -C network   (Note this is showing up as unclaimed)
*-network UNCLAIMED
       description: Network controller
       product: 6000 Series Gen2
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:25:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d4100000-d4101fff

lspci
Network controller: Intel Corporation 6000 Series Gen2 (rev 34)

lsmod
Module                  Size  Used by
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190647  2 vboxnetadp,vboxnetflt
intel
ndiswrapper           184384  0 
intel_agp              26926  0 
e1000e                133436  0 

ndswrapper -l
netwns32 : driver installed
    device (8086:0085) present (alternate driver: iwlagn)

dmesg | grep iwl
[  791.378095] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  791.378098] iwlagn: Copyright(c) 2003-2010 Intel Corporation

---

### Post by ivicks on 2013-01-12
This information might help you. On my HP EliteBook 8560p the wireless is based on (non free) firmware. The error I received is as followed: Wireless firmware file missing, iwlwifi-6000g2a-6.ucode iwlwifi-6000g2a-5.ucode. This error was received on Ubuntu 12.04 and 12.10 also on Debian 7.0 Beta 4.

Once I connected the laptop to the wired network I was able to receive the proprietary drivers which fixed my issue.

---

