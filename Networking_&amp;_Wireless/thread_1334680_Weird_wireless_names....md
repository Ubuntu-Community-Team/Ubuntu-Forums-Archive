---
title: "Weird wireless names..."
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by imac_89 on 2009-11-22
I have an interesting series of wireless networks in my networks list. Thought i would share this with everyone.

This happened after updating to the latest build of Ubuntu 9.10. (I jumped from a subversion of 11 to 14 I think is what i read in my GRUB menu...).

Has anyone else had this happen?

EDIT: The Linux Kernal upgraded from 2.6.31-11 to 2.6.31-14. Why this had an effect on the wireless, I do not know.

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
        Subsystem: Intel Corporation Device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 26
        Memory at ffcff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [e0] Express Legacy Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Device Serial Number a4-ab-84-ff-ff-02-13-00
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945

---

### Post by imac_89 on 2009-11-22
Alright, so all the weird network names have disappeared after I did this:

-- Make my network visible
-- Connected to it with success
-- Made the network hidden again
-- let Ubuntu connect by itself

I honestly don't know why this worked... But I am now getting an actual IP address from my router. ie: 10.0.0.11 compared to 10.1.24.48

Now why i was getting these mucked up network names, I cannot say.

---

### Post by williejones on 2009-11-22
That's strange.  Glad the names are now working, but there must be a glitch to cause the mumbo jumbo you first saw?

---

