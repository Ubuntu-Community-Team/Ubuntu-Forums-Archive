---
title: "Dual NIC's Recently Changed to the Same MAC?"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by xianthax on 2010-03-06
This may get a better answer in the server forum, feel free to move it.

I have dual realtek RTL8111/8168B Gigabit network links on my desktop.

They're setup as a bonded link, this setup has been running fine for ~5months or so now.

Just recently after a reboot, i started having problems.

This was the first time i've rebooted in a long time and i use a 2.26.32 kernel i built in December so there were no changes to the kernel.

The issue appears to be that they both now report the same MAC address.  Previously they were 1 apart, eth0 ending in :c0 , eth1 ending in :c1.  

Now they both report in ifconfig as :c0.

Because of this, udev has renamed eth1 to eth1_rename as udev is looking for the :c1 mac address to name the interface.

This breaks my bonding configuration and causes all sorts of problems, i can't get any connection at all on the bond0 interface as it pops errors when it trys to enslave eth1(which now doesn't exist).  

I have to run dhclient to pick up an IP on the eth1_rename interface to get network connectivity.

I noticed that for some reason ubuntu was loading the r8169 module instead of the r8168 so i snagged the newest r8168 module source and gave it a shot with this driver.  No change at all.

Modifying my bond0 config to bond eth0 and eth1_rename results in a dhcp pick up but no traffic will flow.

Any idea how a network interface would have changed its MAC? and what is the fix for this?

---

### Post by xianthax on 2010-03-07
The Answer:

This is one of the dumbest bugs i've seen in a long time, thank you realtek.

The when the bonding module combines links it sets them all to the same MAC address (the address of the first link).  On a clean shutdown, the bonding module is nice, and resets the MAC addresses as it should.

However,  There is a very lovely bug in the r8169 and r8168 drivers that results in the driver not loading the MAC address from the EEPROM on boot, but rather pulling it from the NIC's memory.  End result: the MAC address doesn't reset on non-clean shutdowns.

Of course this wouldn't have caused a problem if udev didn't define interface names based on MAC addresses.

Solution: unplug computer from the wall for 10 minutes.

Better Solution: udev needs to name interfaces based on the cards serial number, not something that can change like a MAC address and the realtek drivers need to force a read from the EEPROM on boot.  i've head a patch for the realtek driver is out there and may be in the kernel now.

---

### Post by David Tomic on 2010-03-23
Small world ...

I've just been struggling with **exactly** the same problem.

Funny thing is I've been absolutely pulling my hair out trying to work out why *sometimes* it picks up the correct interface name, and not others.

Now it all makes sense though ...

Oh well ... I guess it's time to kill the computer for a few minutes ;)

---

### Post by David Tomic on 2010-03-23
Yep ... just confirming that killing power to the box for a few minutes has "fixed" the problem.

[That is of course, until the next time the machine doesn't shutdown/restart cleanly, and I end up back at square 1 again ...]

---

### Post by isolationism on 2012-07-11
At the risk of re-opening a rather stale thread, I wanted to share one slightly better temporary solution, and a (happily) permanent one for dealing with this problem.

First, if you need to get up and running quickly (and haven't solved this problem permanently yet), getting both network cards to come up quickly so your bonded interface works is as easy as wiping the relevant interface lines in ```
/etc/udev/rules.d/70-persistent-net.rules
``` -- then, when you reboot the machine, the devices will be enumerated again and the bonded interface will start correctly.

However, this is only a reasonable temporary fix; it's better than unplugging the machine and waiting for 10 minutes, but only marginally.

Fortunately, a permanent solution is very easy to effect. As root, run ```
lspci | grep -i eth
``` and remark the numbers at the front of each line. Example:

```

**03:00.0** Ethernet controller: Realtek [...]
**04:00.0** Ethernet controller: Realtek [...]
```

Now, edit ```
/etc/udev/rules.d/70-persistent-net.rules
``` and add a KERNELS== parameter to match the addresses above. You'll have to prepend "0000:" to each:

```

SUBSYSTEM=="net", [...] **KERNELS=="0000:03:00.0"**, ATTR{address}=="00:25:90:02:c1:b0", [...] NAME="eth0"
SUBSYSTEM=="net", [...] **KERNELS=="0000:04:00.0"**, ATTR{address}=="00:25:90:02:c1:b0", [...] NAME="eth1"
```

Now udev will be able to distinguish between the devices despite the fact that they share the same MAC address, and the bonded interface will come up cleanly every time.

---

### Post by wildmanne39 on 2012-07-11
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

