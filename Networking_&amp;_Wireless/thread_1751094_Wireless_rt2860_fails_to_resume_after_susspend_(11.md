---
title: "Wireless rt2860 fails to resume after susspend (11.04, Natty Narwhal)"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by andre_orwell on 2011-05-06
Hi,

I've been happily using this lappie with LTS but wanted to try out 11.04.  It looks great but wireless has been an issue:

1. No wireless during install
2. Had to manually blacklist the rt2860pci etc modules
3. Wireless still not resuming after suspend


05:00.0 Network controller: Ralink corp. RT2860
        Subsystem: Ralink corp. Device 2790
        Physical Slot: 0-2
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2860
        Kernel modules: rt2860sta, rt2800pci


FWIW:
cat /etc/pm/config.d/config 
SUSPEND_MODULES="rt2860sta"

The latter manual mod improved things slightly but still no cigar :-(

Any advice much appreciated.

---

### Post by andre_orwell on 2011-05-13
Well I've tried just about every lead I can find in the forum. Compiled and installed the driver from ralink, also changed the firmware for the latest version on the ralkink site, changed boot options.  Always my system gets stuck authenticating after a sleep - resume cycle and needs a reboot to work again.

Dropping back to 10.04 for the time being.

Thanks for everyone who has posted their working.

---

### Post by irv on 2011-05-13
I also had a problem with my wireless card a Broadcom 4311, but I got it working after some time. Here was my fix.
[http://ubuntuforums.org/showthread.php?t=1742147&page=4]("http://ubuntuforums.org/showthread.php?t=1742147&page=4")

I don't know if you are having the same problem I was having, but just thought I would pass this on.
I also was thinking about going back to 10.10, but then I got it fixed.

---

### Post by andre_orwell on 2011-05-14
Thanks irv, I think I've pretty much covered that space in my experimentation.  The one thing I didn't try was the non STA drivers.  For rt2860 the posted wisdom was that the pci drivers should be blacklisted and that using the STA drivers generally solved performance and connection issues.  I've not had performance or connection issues at all since blacklisting.  The only issue has been failure to reconnect after suspend.

Not sure where to look anymore.  If anyone has hints I can help debug but so far I've not had much response.

---

### Post by andre_orwell on 2011-05-14
Not very satisfying but... I stuffed my install when I deleted network manager.  I did a complete re-install connected to a wired network (so it installed all updates and reinstalled packages).  Now it works.  Go figure

:popcorn:

---

### Post by irv on 2011-05-15
I found this posted in another thread:
> The solution to the wireless freeze is to upgrade to the latest kernel 2.6.39.0.

It brings a lot of new features and Natty is no longer a crippled beast tethered to an Ethernet cable.

The 2.6.38.8 kernel Natty ships with was buggy and connecting to a wireless network would freeze up the desktop, necessitating a hard reset.

Sometimes a kernel upgrade is definitely needed. The difference is remarkable, particularly with Unity!
Maybe this is what happen in your case when you did a update.

---

### Post by andre_orwell on 2011-05-16
Well that's good news.  I actually found out what was going on thanks to this post on launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/689004](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/689004)

It all worked for me after the reinstall because I was plugged in to power. Disabled power management for wireless and pcie_aspm.  Now it seems to work untethered.

thanks, might check out a kernel upgrade.

---

### Post by andre_orwell on 2011-06-14
Just to complete this thread I thought I'd add that I installed the 2.6.39 kernel and it made no difference to my network problem.  I still had to use the sta drivers (blacklist 2800pci) and disable power management by
```

sudo touch /etc/pm/power.d/wireless
sudo touch /etc/pm/power.d/pcie_aspm

```
in order to get everything to function correctly through suspend and resume cycles.
Cheers,

---

