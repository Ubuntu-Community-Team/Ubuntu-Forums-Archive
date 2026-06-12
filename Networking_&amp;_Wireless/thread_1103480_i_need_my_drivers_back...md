---
title: "i need my drivers back.."
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by rudi009 on 2009-03-22
yesterday i was patching my drivers of the wireless card..well don't ask why(earlier was also not working properly) and i now i'm stuck. i need the old drivers back for my intel 3945abg wireless card(or somthing new if that works..the problem with the old one was that i could start wifi only after putting my laptop on standby once!!)..lspci -v |less shows this:

01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Device 135b
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 71300000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: ipwraw
        Kernel modules: ipwraw, iwl3945

please help..

---

### Post by rudi009 on 2009-03-22
ok.. i've  found the driver but now how to install it..its 'ipw3945'

---

