---
title: "WLAN drops on VT switch (LiveCD)"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by xerces8 on 2010-10-12
Hi!

I booted the Ubuntu 10.10 desktop i386 CD into the Live environment and connected to a WLAN AP (using WPA2).

If I switch to VT1 by pressing ctrl-alt-F1, the connection is dropped.
In syslog NetworkManager lists a device state change 8 -> 3 (reason 38).

When I go back to X (alt-F7), NM starts to reconnect and succeeds in a couple of seconds.

Is this on purpose?
Or a bug?

It happens on two PCs I tried (one laptop with builtin Intel WLAN, other a desktop PC with USB WLAN adapter Belkin F5D 7050 v4004, I think ZyDAS chipset) so it is not HW fault.

Regards,
David

---

