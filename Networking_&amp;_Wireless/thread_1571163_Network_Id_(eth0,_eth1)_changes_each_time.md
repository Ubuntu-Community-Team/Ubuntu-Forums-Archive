---
title: "Network Id (eth0, eth1) changes each time"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by locoHost on 2010-09-09
My network name (eth0 or eth1) set for the Broadcom wireless on this Dell E1705 changes/swaps nearly every time I start up. Normally this would not be an issue but it confuses my Conky script ;) How can I force the name to stay the same on each reboot?

Thanks everyone :)

---

### Post by SlugSlug on 2010-09-09
maybe try disable onboard LAN in BIOS

---

### Post by endotherm on 2010-09-09
I've seen this happen before, but usually over an os reinstall. I've never seen it happen over a reboot, but I'm sure someone has.
do you use dhcp or static addressing? if dynamic, I would just make sure both interfaces are in network-manager, and set them both to DHCP. that way, the software interface doesn't matter, and whatever card is plugged in will get an address. but your right, that won;t help conky...
i wonder if it wouldn't be easier to write a script that returns the name of the active interface. then your conky config could just call it, instead of hard coding the dev name. hmmmm.

---

### Post by locoHost on 2010-09-09
> **endotherm said:**
> i wonder if it wouldn't be easier to write a script that returns the name of the active interface. then your conky config could just call it, instead of hard coding the dev name. hmmmm.

That's an interesting thought. Again the name doesn't matter except to Conky.

I was hoping maybe there was a quick network config fix.

---

### Post by locoHost on 2010-09-09
There was no wired connection defined in network manager. I just did that. I'll reboot and see what happens. Maybe doing this, the wired connection will now consistently get eth0 and the wireless will get eth1.

---

