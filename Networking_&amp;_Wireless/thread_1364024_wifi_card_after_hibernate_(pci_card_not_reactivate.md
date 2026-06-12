---
title: "wifi card after hibernate (pci card not reactivated)"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by w2vy on 2009-12-25
I have a Dell Inspiron 1100 with a dell wifi card (PCMCIA card)

When I resume the card does not appear to get powered up.

I have to remove and re-insert it to get power applied.

I am now running 9.10 in the last big upgrade (I guess to 9.04)
I had a problem and found the solution, but made no posts and forgot
what I did...

I believe I added 

STOP_SERVICES="networking"

to /etc/default/acpi-support

I just noticed

ENABLE_LAPTOP_MODE=false

I changed it to true and will reboot and report back if it helped.

I also see # LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)

Maybe this is new and is why things are working differently...

Is there a different place we need to change things?

-----
Rebooted and the hibernate/resume.

No change... any ideas?

tom

---

