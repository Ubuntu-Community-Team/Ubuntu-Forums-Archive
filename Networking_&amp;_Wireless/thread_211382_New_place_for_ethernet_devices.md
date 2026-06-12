---
title: "New place for ethernet devices?"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by bartbes on 2006-07-08
After some problems, I got my system back up. But I've lost my Internet/network connection. It can't find my network adapter anymore (It does in device manager) so to post this I'm working on 5.05 live. After reading MAKEDEV man pages I saw that the Network devices aren't in the /dev dir anymore, so where did they go?

---

### Post by bforbes on 2006-07-08
Post the output from lspci and the contents of /etc/network/interfaces.

---

### Post by bartbes on 2006-07-08
I hope it's ok that I've chrooted in the install and then did lspci -v
Here is the output (I've only copied the network card):
> 0000:00:11.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at c800
        Memory at dffeff00 (32-bit, non-prefetchable)
        Capabilities: [50] Power Management version 2


and here is /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

```

---

### Post by bartbes on 2006-07-08
-

---

### Post by bforbes on 2006-07-08
Post the output from
```

ifconfig

```

---

### Post by bartbes on 2006-07-09
I didn't do that now, but I did do that before.. only devices are:
lo
vmnet1
vmnet8

(vmnet1 and 8 are from VMWare server)

---

### Post by bartbes on 2006-07-09
I figured out it might be because I'm using an old kernel.
I've upgraded from BB to DD but my new 2 kernels say something about my BIOS that doesn't support my 2nd HDD

EDIT: I figured out it says that there are too much cylinders.. (see [this thread](http://www.ubuntuforums.org/showthread.php?p=1232190) to see how I'm going to fix that and how I discovered that)

---

### Post by bartbes on 2006-07-10
With a new boot partition I can now start the new kernels, internet is working again!

---

