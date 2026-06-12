---
title: "70-persistent-net.rules not being applied after upgrade to karmic"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by humble_coffee on 2009-11-12
Upon upgrading from Ubunto 9.04 to Ubunto 9.10 I'm now experiencing problems with the naming of my network interfaces.

I have two ethernet ports which were previously named eth0 and eth1. After upgrading to Karmic, the interface names are all over the place. It started by apparently renaming eth0 to eth0_rename. Since then I've tried to fix things by fiddling with the Network Connection manager. Results have varied somewhat, with success on one occasion, then failure with the "eth0" and "eth1" names being assigned but to the wrong ethernet ports. My symptoms are now back to the eth0_rename.

The thing is, looking at the lines in 70-persistent-net.rules, the NIC with the MAC address that is meant to be assigned to eth0 is actually being named eth1 and the NIC with the MAC address that is meant to be assigned to eth1 is being assigned eth0_rename.

Here's the contents of my /etc/udev/rules.d/70-persistent-net.rules (I haven't manually edited them at any point)

# PCI device 0x10ec:0x8167 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:fc:e1:6e:ec", ATTR{type}=="1", NAME="eth0"

# PCI device 0x11ab:0x4364 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:fc:e1:7a:d7", ATTR{type}=="1", NAME="eth1"

# USB device 0x0bda:0x8187 (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:15:af:22:df:99", ATTR{type}=="1", NAME="wlan0"

As you can see, there's no duplicate entries. Everything I've read that relates to this problem talks about correcting these rules to fix the problem, but I can't see what's wrong with them.

---

### Post by Iowan on 2009-11-12
You could edit the file and see if changes stay put...

Or you're saying the information in */etc/udev/rules.d/70-persistent-net.rules* is right... but doesn't get assigned that way?

---

### Post by humble_coffee on 2009-11-12
> **Iowan said:**
> Or you're saying the information in */etc/udev/rules.d/70-persistent-net.rules* is right... but doesn't get assigned that way?

Yep.

---

### Post by humble_coffee on 2009-11-15
Also, other people are having this problem too. 

There is another post about the same problem [here]("http://ubuntuforums.org/showthread.php?t=1312938"). I started this post as the other one was incorrectly labeled as being solved.

---

### Post by mstombs on 2009-11-16
I also have this problem.

The whole point about having persistent-net.rules is that the order in which devices are detected by the kernel is deterministic and not predictable.  But the rules are not working.

On my system, ASUS mboard with dual Ethernet, which sometimes hangs on reboot (after upgrade it was totally unusable, this if after complete re-format re-install) I can see the error message - udev fails to correct the device name because "device is in use or busy" or something very similar.

Searching the internet this seems to have been a problem 5 years ago, but it is not clear if the current problem is the kernel version, udev or Ubuntu's Network Manager which also gets confused with interface name/mac address randomly changing

---

### Post by humble_coffee on 2009-11-16
Wow this is annoying. It seems like they're swapping around on each boot. 

Here's what udev did on this particular boot:

```
$ dmesg | grep udev
[   12.911633] udev: starting version 147
[   16.371610] udev: renamed network interface eth1 to eth0
[   16.394903] udev: renamed network interface eth0_rename to eth1
```

I predict that next time one of them them will be changed back to eth0_rename.

---

### Post by mstombs on 2009-11-24
Examining the logs on my PC it is clear the problem is that Network Manager sees the interface before udev, and udev fails to do the rename because the interface is already in use by dhclient etc.

Upgrading the kernel to that in "proposed"

```
Linux ubuntu 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux
```

seems to fix the problem for me, udev does its job much earlier - example

```

Nov 24 08:06:34 ubuntu kernel: [   10.505634] udev: starting version 147
Nov 24 08:06:34 ubuntu kernel: [   10.513746] lp: driver loaded but no devices found
Nov 24 08:06:34 ubuntu kernel: [   10.584760] nvidia: module license 'NVIDIA' taints kernel.
Nov 24 08:06:34 ubuntu kernel: [   10.584765] Disabling lock debugging due to kernel taint
Nov 24 08:06:34 ubuntu kernel: [   10.593977] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 24 08:06:34 ubuntu kernel: [   10.619785] ppdev: user-space parallel port driver
Nov 24 08:06:34 ubuntu kernel: [   10.620458] parport_serial 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 24 08:06:34 ubuntu kernel: [   10.620484] parport0: PC-style at 0xe800 [PCSPP,TRISTATE,EPP]
Nov 24 08:06:34 ubuntu kernel: [   10.633503] udev: renamed network interface eth1 to eth0
Nov 24 08:06:34 ubuntu kernel: [   10.636154] Adding 11871992k swap on /dev/sdb5.  Priority:-1 extents:1 across:11871992k 
Nov 24 08:06:34 ubuntu kernel: [   10.653238] udev: renamed network interface eth0_rename to eth1
```

so my assumption is that this problem is kernel, not udev or Network-Manager

---

