---
title: "no luck switching NIC's, have I tried everything?"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by chconnor on 2009-01-16
Hi -

We have 8.04 server installed on an old machine.

Network card it had in it works fine, but it doesn't support wake-on-LAN, which is what we need.

We've tried two other net cards, neither of which seem to work (in linux, in windows, at least one does).

One card (can't recall the brand) has the RealTek 8139C chip. The other is a 3-Com 3C905-TX.

We've tried the various module tricks for the 8139 (removing a module to force use of module 8139too), tried running it in Windows (works fine) and then pulling the power plug out so that Windows won't leave it in a bad state.

Tried booting with acpi=off (which is not a choice anyway because we need to be able to remotely hibernate/shutdown this machine). Tried the "noapic" option (for the 8139 I think it was). None of this has any effect.

Both cards are recognized properly by lspci. But after booting, there is no eth0. "/etc/init.c/networking restart" gives a series of errors (I can paste the details if useful). Obviously none of the ifconfig type commands work as there is no eth0 device. ifconfig reveals only "lo".

When we swap the original card in, all is well.

We've tried a couple PCI slots.

Something is telling me it's not the cards, and that we're leaving out a step? I heard about /etc/iftab causing issues, but maybe that was legacy advice; there is no /etc/iftab on our system.

Have we tried everything? Is it just the age of the motherboard (circa mid/late 90s)? Is there some lower-level memory the system has of the original card that is preventing the others from working?

Thanks for any tips/links/direction!

-c

---

### Post by cariboo on 2009-01-16
Both cards are well supported in Linux, you seem to have spent a lot of time on the 8139 card, what happens with the 3Com card?

Jim

---

### Post by chconnor on 2009-01-16
> **cariboo907 said:**
> Both cards are well supported in Linux, you seem to have spent a lot of time on the 8139 card, what happens with the 3Com card?
Jim

Yeah, that was my impression too, and why i suspect something else may be afoot...

I've tried basically all the stuff I described above (except the 8139-related module of course) with both cards. Same thing. Shows up in lspci, and the appropriate modules seem to have been loaded (lsmod), but no eth0, and doing a networking restart doesn't work...

Thanks,
-c

---

### Post by chconnor on 2009-01-20
Aha. This was the issue:
[http://ubuntuforums.org/showthread.php?t=955990&highlight=replace+nic](http://ubuntuforums.org/showthread.php?t=955990&highlight=replace+nic)

The (auto-generated) file:
/etc/udev/rules.d/70-persistent-net.rules
caused the server to remember its last MAC address any time the card is switched.

I'm sure there's a very good reason for this. :-)

Now the problem is that the various cards we're trying now (3com 3c905 type cards) don't report themselves as able to Wake-on-LAN to the 3c59x module, apparently. ethtool reports nothing about Wake-on-LAN for them. They do support it (the WOL cable dangling off of them, connected to our mobo, proves it.)

I've tried using "options 3c59x enable_wol=1" in /etc/modprobe.d/options, no change.

I'll start another thread, probably, since this is now off-topic...

-c

---

