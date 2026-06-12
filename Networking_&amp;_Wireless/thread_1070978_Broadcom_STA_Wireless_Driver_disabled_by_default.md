---
title: "Broadcom STA Wireless Driver disabled by default?"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by RedPenguin on 2009-02-15
I have a Compaq Presario F7W39M laptop that has a Broadcom Wireless NIC and even though the wireless card works with the Broadcom STA Wireless Driver in Restricted Drivers, if I do a reboot, suddenly the wireless card is not working.

When you go to Device Drivers, it has a checkmark to use the driver but then it's stating not in use. Once I disable and re-enable, it works again.

---

### Post by kevdog on 2009-02-15
I would conjecture its a problem with the wl driver not loaded at boot and possibly a conflict with b43/ssb modules being loaded.  First thing I would check is that wl is loaded after booting by checking lsmod.  I would also take notice if any other conflicting modules are being loaded such as ssb/b43.  You could also post lshw -C network (or at least save the results to a file), and then post these results once you have the network up and running to help us out!

---

### Post by RedPenguin on 2009-02-15
> **kevdog said:**
> I would conjecture its a problem with the wl driver not loaded at boot and possibly a conflict with b43/ssb modules being loaded.  First thing I would check is that wl is loaded after booting by checking lsmod.  I would also take notice if any other conflicting modules are being loaded such as ssb/b43.  You could also post lshw -C network (or at least save the results to a file), and then post these results once you have the network up and running to help us out!

It looks like it was wl.

I added wl in to /etc/modules because it was not loaded by default.

I then rebooted and wireless works by default now.

---

