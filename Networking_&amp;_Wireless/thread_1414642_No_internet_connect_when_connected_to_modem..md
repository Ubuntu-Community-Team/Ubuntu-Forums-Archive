---
title: "No internet connect when connected to modem."
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by spoolboyy on 2010-02-23
I am having the same issue.  Here's some information from my troubles, not sure if Darkstar's are similar.

Ubuntu 9.10 32-bit
Intel Ethernet adapter
Tried connecting via Router and directly into the Cable Modem

Brand new install of Ubuntu from CD, can't get any internet access, plugged directly into my Cable Modem or through the router.  The rest of my network (3 PCs and a printer) DO have connectivity, I haven't experienced this problem with any Ubuntu distro in the past, help!

-Adam

---

### Post by Iowan on 2010-02-23
@spoolboyy:
Separate thread may be forthcoming...
Does machine get IP address? DHCP? Results of **sudo lshw -C network** and **route -n**?

---

### Post by spoolboyy on 2010-02-28
The machine SOMETIMES gets a connection, if I continue asking the machine to connect to eth1 (the machine has two ethernet cards, one on the mobo (eth1) and a PCI card, (eth0))

When the machine fails to connect, route -n produces only the column headers....

when I run it an the connection IS working properly, i get this:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1     

```

---

### Post by spoolboyy on 2010-02-28
When I run:  sudo lshw -C network, the computer prints the following to the screen...

```

PCI (sysfs)

```

...and then it freezes up, and I have to shut down the PC using the power button.

Help?

---

### Post by Iowan on 2010-02-28
My machines pause for a few seconds after the "PCI (sysfs)" message. Have you tried removing the eth0 (PCI) card?

---

### Post by spoolboyy on 2010-03-01
I actually installed the card after the OS installation the first time.  It didn't resolve the problem, so I reinstalled with the card installed on the motherboard, still no luck, card in or out.

I managed to install all of the updates (piece meal, a few at a time) while my connection worked intermittently.  So far, so good, the PC seems to be keeping its connection.

I'll update this thread if any issues return.

-spooly

---

