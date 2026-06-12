---
title: "Wake on LAN/hibernation/ACPI quandry... works in WinXP, not Linux?"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by chconnor on 2009-01-22
Hi there -

using Ubuntu 8.04 server...

We are using a 3Com 3c905B-TXMBA card with a wake-on-LAN cable connected to our mobo.

Trouble is, ethtool doesn't show anything for the wake-on-LAN support (though it does support WOL).

(Starting in WinXP, enabling WOL, and pulling the plug (a trick I read about for some cards) had no effect.)

I modified 3c59x.c to always set WOL on the card, regardless of what it believes it should do, etc. Recompiled, etc, had no apparent effect.

I can wake it up when i boot into windows and then "stand by" or "hibernate". Thus, i suspect that my hibernation in linux is not setting things to the right acpi state, or that the driver (with or without my mods) is not working.

When it's hibernated, the link lights on the card are active, if that means anything.

I'm using the hibernate script. Just doing "hibernate" to hibernate it. I don't have tuxonice or anything like that, so I assume it's using swsusp, under default settings?

Any thoughts on what to check re: ACPI, or anything else?

Thanks very much,
-c

---

### Post by ForgetLogic on 2009-01-22
Hi -

I'm new to posting though I've used these forums extensively and successfully setting up my new build.  I've got Intrepid Ibex running on a 64bit ASUS board.  I have to say that I'm quite impressed.  My last foray into linux was probably sometime around '03 (date of my last build), and this experience was significantly easier.  In fact, my dual boot to Vista has been relegated strictly to gaming, and OS debug.  So I guess, kudos guys.  I'm impressed.

Here's where I'm at.  I've successfully brought up an ssh server, with dynamic hosting via dyndns.  I'd like to be able to throttle my power consumption remotely either bringing it down to a hibernating or halted state, hence the thread selection.

State of Efforts:
I've updated my device using ethtool to enable WOL, and enabled it in the bios.  This is a sourced part of my /etc/init.d.  The script is as follows:

#!/bin/bash
ethtool -s eth0 wol g
exit

I've got a intel powerbook from which I am broadcasting magic packets successfully.  When I shut down the machine from my vista boot, it works, from ubuntu... nope.

This is what I've tried:
editing the /etc/init.d/halt script to set netdown=no.
broadcasting the reverse mac address i.e. 01:23:45:67:89:ab > ba:98:76:54:32:10
kill nmapplet before halting

I've also tried hibernating... unfortunately, this is causing a crash.  I'm thinking this must have something to do with the power management software not interfacing properly with the hardware to negotiate a lan boot from various states.  It complained about being unable to shutdown the nic.  I'm hoping somebody somewhere has found some magic workaround which has somehow disappeared from the forums.

I'd like to try anything you all can suggest to help figure this out.  Just prepare for me to be a bit n00b.

---

### Post by chconnor on 2009-01-23
Incidentally, I've tried removing "-i" from the /etc/init.d/halt command, I've tried "rmmod -f 3c59x" and "update-initramfs -u" before shutdown, I've done "hibernate" and "shutdown -h now", tried the reverse-MAC, tried different PCI slots...

My understanding is that windows hibernates to S4 and swsusp hibernates to S5... At first I was guessing my mobo/bios doesn't support WOL from S5, but occasionally, when swapping net cards around, I'd forget to pull the power plug, and when i removed the NIC with the WOL cable still attached and the computer in S5 (AFAIK), the computer would spring to life, so I think it's not that...

I've also messed with /etc/acpi/wakeup to no success... (echo PCI0 > /etc/acpi/wakeup)

I'm thinking I should post this at the end of the monster WOL thread at
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

...but any input very welcome.

I'd love to avoid recompiling the kernel to use TuxOnIce. Perhaps my next step is to track down a different NIC that has a better-functioning driver...
-c

---

