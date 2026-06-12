---
title: "Wireless card disappears!"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by Leslie Viljoen on 2010-02-16
Hi everyone

Today, my wireless network card just disappeared. Its an Intel Wireless 5300 AGN which uses the iwlagn driver. The driver doesn't load, and though I can successfully modprobe it, that makes no difference. "lshw -C network" shows no mention of the card. lspci doesn't show anything either.

I have tried booting from an older kernel, makes no difference. So at this point I am wondering if the card is actually broken. Is there anything else I can check? Is IS enabled in the BIOS setup.

Current kernel: Linux lesliev-laptop 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux
Running Ubuntu Karmic on a HP 6730b laptop.

---

### Post by Cabs21 on 2010-02-16
you didnt accidentally turn off your wireless card from the outside of the laptop right?

---

### Post by Leslie Viljoen on 2010-02-17
> **Cabs21 said:**
> you didnt accidentally turn off your wireless card from the outside of the laptop right?
Alas, no! I can press the little button to do that, and bluetooth gets enabled and disabled (I can see it in syslog). But wireless is not mentioned.

---

