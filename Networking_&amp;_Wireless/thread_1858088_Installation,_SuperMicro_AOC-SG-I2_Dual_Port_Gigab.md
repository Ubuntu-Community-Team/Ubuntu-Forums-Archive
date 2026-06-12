---
title: "Installation, SuperMicro AOC-SG-I2 Dual Port Gigabit NIC PCI-E Card"
date: 2011-10-11
forum: Networking &amp; Wireless
---

### Post by jdpond on 2011-10-11
This was for Ubuntu 11.04, but I'm assuming the problem predated this version and is probably applicable to subsequent versions (and possibly other distros) too.

Problem: Drivers must be downloaded and manually configured
Device: SuperMicro AOC-SG-I2 Dual Port Gigabit NIC PCI-E Card

I just installed a dual port (Gigabit) interface from SuperMicro and thought I would pass on the experience.  You can start with [the instruction manual]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBoQFjAA&url=http%3A%2F%2Fwww.supermicro.com%2Fmanuals%2Fother%2FAOC-SG-I2.pdf&ei=WniUTuvzG4TX0QGJueTNDA&usg=AFQjCNG5hS4EDWo7VRYHRg3QQqCAeicLAg&sig2=SSm_1Rx2Pggl5SlIuxkd8A"), but it took quite a bit more for me.

To install the driver, I needed to:

[LIST=1]
[*]Download, Compile, Install the driver
[*]Manually Fix the Persistent Network Rules to Resolve Duplicate Device Name
[/LIST]

[SIZE="2"][FONT="Arial Black"]Download, Compile and Install the Driver[/FONT][/SIZE]

This card uses the Intel 82575EB chipset, which you can discover by following the [instructions from Intel]("http://www.intel.com/support/network/sb/cs-008441.htm").  Specifically, use the [Network Device and Driver Information Utility for Linux]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17289") listed on that page - but if you do be aware that Intel in its infinite wisdom has used Windows line endings, so you'll need to [fix that ]("http://www.debianadmin.com/flip-convert-text-file-line-endings-between-unix-and-dos-formats.html")before running the source file.

You'll also need to get some tools (if you don't already have them):
```

sudo apt-get install build-essential ethtool [flip]

```

Once you've got the tools you need (and converted the downloaded Intel tool), run the utility:

```

sudo bash netdriverinfo.sh

```

Somewhere in there you should get something like:

```

: 01:00.0
    Make/Model = Super Micro Computer Inc Device 10a7
    Ethernet controller = Intel Corporation 82575EB Gigabit Network Connection
    VenID:DevID = 8086:10a7

```

The important part of this is the "82575EB" portion.  Use this (or whatever you find) to search the Intel site for the appropriate driver set, then download it.

At the time, it was [here for the igb driver 3.2.9]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=13663&lang=eng&wapkw=(82575EB)").  You can compile it following the [instructions here]("http://downloadmirror.intel.com/13663/eng/README.txt"), but at the time it was basically:

```

tar zxf igb-3.2.9.tar.gz
cd igb-3.2.9/src
sudo make install
sudo modprobe igb
sudo ifconfig -a

```

Now while this compiled and installed the driver, it did something funny - assigned the same name device name to both MAC addresses.

The ifconfig -a command showed a device with a dup name (in my case "eth1-eth2"), which really messes stuff up.

To fix this, see the next step.

[FONT="Arial Black"][SIZE="2"]Manually Fix the Persistent Network Rules to Resolve Duplicate Device Name[/SIZE][/FONT]

For some reason, during the "autodiscovery", the driver or Ubuntu assigned a duplicate name to the two devices on the card.

To correct this, you'll need to modify the persistent network rules by:
```

sudo vim /etc/udev/rules.d/70-persistent-net.rules

```

The duplicate name was immediately apparent (and fixable) by modifying the "NAME=" portion after identifying which were the desired MAC addresses.

I hope this helps save you the 8 hours or so it took me to figure it out - GOOD LUCK!

---

