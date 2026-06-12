---
title: "Help with network hardware settings file location"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by xkaliburx on 2009-05-01
Think it's a MAC issue, as I am coming from the redhat world.  Well I have setup a great new box running ubuntu-server 8.10 64bit and need to roll this out to a few other box's.  I cloned the machine (using clonezilla) and worked perfect.

On restart, I changed hostname, and IP's in the interfaces file, but it's not starting up.  An ifconfig just shows the local lo address. The server hardware is nearly identical, their Dell poweredge servers one model diff, in redhat in the network settings there does show the hardware MAC which is where I think my problem is.

** UPDATE **

using dmesg I saw the following;
dmesg | grep -i eth0
[ 3.582327] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[ 7.218819] udev: renamed network interface eth0 to eth3

SO I changed the interfaces file to auto eth2 and eth3 and low and behold it worked.  I would like these (for consistency) to be 0/1, so I am looking at the /etc/udev/rules.d/70-persistent-net.rules and see the following;

# PCI device 0x8086:0x1076 (e1000)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:14:22:0d:dc:89", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x1076 (e1000)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:14:22:0d:dc:8a", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x1076 (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:15:c5:5d:2c:2a", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x8086:0x1076 (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:15:c5:5d:2c:29", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"


I tried as you see commenting things, renaming the 2/3 to 0/1 but no good.

Anyone can help on this, it's much appreciated

---

### Post by Iowan on 2009-05-01
I've never used clonezilla, but wonder if it copied original MAC addresses. Check **lshw -C network** for actual MAC addresses (unless you already know them). Make a backup copy of */etc/udev/rules.d/70-persistent-net.rules*, then delete the entries that don't match your devices. Edit the real ones to eth0/1.  Good luck!

---

