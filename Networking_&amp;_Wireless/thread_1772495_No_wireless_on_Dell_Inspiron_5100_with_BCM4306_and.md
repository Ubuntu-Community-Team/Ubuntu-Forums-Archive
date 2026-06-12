---
title: "No wireless on Dell Inspiron 5100 with BCM4306 and b43legacy driver on 10.04"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by zshift on 2011-05-31
I cannot get the wireless to work on a Dell Inspiron 5100 with BCM4306 and b43legacy driver on 10.04.

I have tried installing b43-fwcutter, but this doesn't make anything work better.

I can create ad-hoc networks, but I cannot scan for networks using iwlist wlan0 scan (no results), and I cannot connect to any networks, even if the essid and mac are provided to iwconfig. wlan0 shows up with the correct information, and device vendor and id are 14e4:4320. Just installed 10.04 (for LTS) and completely updated through ethernet.

Update: I tried the instructions at [http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy](http://linuxwireless.org/en/users/Drivers/b43#fw-b43legacy), still no luck.

Update: following the instructions at [http://www.ubuntuforums.org/showthread.php?t=780692](http://www.ubuntuforums.org/showthread.php?t=780692) I noticed the following issue:

When I run **lshw -C network**, I receive the following output:

>   *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:11 memory:faffc000-faffdfff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:6f:23:f2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


Notice that under the configuration section, I do not have a specified module. All of the guides that I've read specify that the module should be **module=ssb**, but I don't know how to set it as such. Any ideas?

---

### Post by Bernmeister on 2011-12-15
This may help: [http://ubuntuforums.org/showthread.php?p=11539545#post11539545]("http://ubuntuforums.org/showthread.php?p=11539545#post11539545")

---

