---
title: "Boot Stops, Displays &quot;Waiting for Network Configuration&quot;"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by buzzingrobot on 2013-08-27
I did a new 13.04 installation on a laptop using a wired eth0 connection.  Now, when the machine reboots with the eth0 cable unconnected, the boot stops and displays "Waiting for Network Configuration".

If the cable is then plugged in, the boot will eventually continue.

Wireless works fine.

So, two question:

1.  How do I get rid of that message and boot without the wired eth0 connection?

2.  The machine will use wireless most of the time, but I'd like it to automtatically switch to wired eth0 when the cable is connected.  Doable?

Here's the contents of /etc/network/interfaces"

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

Thanks.

---

### Post by praseodym on 2013-08-27
Why is it configured via the interfaces file? Open it via
```

gksudo gedit /etc/network/interfaces
```
remove both lines with "eth0", save, close the editor and reboot.

---

