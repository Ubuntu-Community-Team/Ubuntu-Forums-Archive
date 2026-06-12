---
title: "eth5 No Network"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by romeroagnelli on 2009-06-26
I have run into a severe problem - I am using Turnkey Linux Appliance [WordPress] Based on Ubuntu 8.04.

I run the appliance on a XP system with virtual box.

Recently, i exported the Virtual Machine as an appliance and then imported it at my office. Once imported, it turned out that now instead if eth0 it configured eth1.

Next time i did the import export process, it went from eth1 to eth2 and so on ... Its now at eth5 - I would have let it work the way it is now, except that it now doesn't work at all!

I tried the following commands:
```
1. \etc\network\interfaces [USED MANUAL EDITING]
2. lshw -C network [THIS COMMAND DOESN'T WORK]
```

Turnkey Linux has a configuration console that is loaded up at every boot. The console is coded in Python which i don't understand, but I'll post the coding if anyone wants.


Problem : My virtual system [Uses Bridged Networking] has absolutely no connection. The TurnKey Linux Config Console gives an error screen with just this 'eth5'.

---

### Post by romeroagnelli on 2009-06-26
Pleas someone! Please reply here! I've been banging my head against the system for ages! Its now at eth9!

---

### Post by romeroagnelli on 2009-06-26
Here's the solution:
There's a stupid file in the /etc directory that keeps a record of MAC addresses of all the Network Adapters. Every time I exported and then imported it registered a new interface ... I hate that file.

SOLUTION:
```
Open /etc/udev/rules.d/70-persistent-net.rules
```

And you'll find something like this:
```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x1022:0x2000 (pcnet32)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:27:dc:f7:84", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1022:0x2000 (pcnet32)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:27:2a:6a:54", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x1022:0x2000 (pcnet32)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:27:8c:75:5b", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x1022:0x2000 (pcnet32)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:27:d4:49:22", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"
```

That's it. Copy MAC Address of the card that you want to use ... Or if you can't change MAC Address, edit them in the file. That solved my problem.

For beginners, I used the following commands:
```
cd /etc/udev/rules.d
nano 70-persistent-net.rules
```

That's it!

And thanks to everyone for being so responsive...I knid of get absolutely no replies on this forum!

---

### Post by cleanden on 2010-04-15
I am noticing the same problem, but I found that editing /etc/network/interfaces and changing eth0 to eth1, or eth1 to eth2, etc. was an easier way to go.

Anyone know of a way to avoid this or fix it in a more automated fashion?

Alex

---

