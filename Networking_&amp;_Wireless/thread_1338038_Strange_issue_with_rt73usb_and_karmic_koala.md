---
title: "Strange issue with rt73usb and karmic koala"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by enrico_pv on 2009-11-26
I installed karmic koala on 2 PCs having a D-LINK DWL-G122 wireless adapter.
THe USB device is recognized (output of lsusb)

- Bus 002 Device 002: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]

And the correct driver (rt73usb) is loaded and everything works fine (I see all the wireless networks around and I can connect to mine).
Both the PCs can see the router (192.168.0.1) and then surf through the web.
Let's call PC_A the first PC (192.168.0.2) and PC_B the second one (192.168.0.3). I'm assigning static IP for these PCs.

The strange thing is that in a non deterministic wave (but in general after some time that the PC is not used) it happens that PC1 may not see PC2 (ping 192.168.0.3 from PC1 gives "no route to host") and/or viceversa. But ping 192.168.0.1 (and then internet navigation) is always available also in this condition.

My first guess is that the wireless adapter (or the loaded module rt73usb) goes in some kind of "sleep mode", but only about "intranet" and not internet.

I have a third PC, let's call it PC3 (192.168.0.4), with a different wireless adapter but the same settings, and it can always be pinged by the other PCs of the local network.

So in conclusion the 3 PC always can navigate but while PC3 is always pinged with succed from the other PC of the local network), PC1 and PC2 are always connected to internet but sometimes they can't be reached by PCs belonging to the same local network.

netstat -rn from PC1 or PC2 gives me

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0

whatever is their condition (they can be pinged or they cannot)

Any advice about this strange issue (that prevent me to correctly share disks between PC belonging to the same local network)?

Thanks,
Enrico

---

### Post by enrico_pv on 2009-11-28
The issue described before has been fixed, although it is not clear to me how I did.

1) apt-get install linux-backports-modules-wireless-karmic-generic
This update the module rt73usb to the version 2.3.0
2) I updated the firmware of the router I'm using in my local networ (netgear DG384v3)
After that, I observet that the issue above described (no route to host....) was happening not so often as before
3) I removed, purged, and install back samba without modifying the smb.conf (strange errors in /var/log/samba(
It seems that action number 3 fixed the issue, although it looks not easy to understand why.

Thanks,
Enrico

---

