---
title: "restricted wireless cards"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by pcox on 2009-09-17
I downloaded ubuntu 8.10 and the wireless works fine, but seeing as how there is an updated 9.04 version I would like to download that, however I did (eariler) and the wireless card was not working.

Why is it that in 9.10 it does not work, I have heard of some restrictions with copyrighted wireless cards (i have an hp pavilion dv5) with some different computers.

Should I stick with ubuntu 8.10 and keep wireless or should I upgrade to 9.04?

furthermore, can you help me find out why my wireless card does not work with 9.04?

please I really want to upgrade but wireless is a big deal to me.
(the wired LAN works fine in 9.04)

Thanks for the help

edit

this is my card i think
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
        Subsystem: Hewlett-Packard Company BCM4321 802.11a/b/g/n Wireless LAN Controller
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at db700000 (64-bit, non-prefetchable) [size=16K]
        Memory at d0400000 (64-bit, prefetchable) [size=1M]
        Capabilities: <access denied>

---

### Post by t0mppa on 2009-09-18
Did you just try the LiveCD of 9.04? There are sometimes differences between that and a real install. And the not working part would probably be a simple case of not having downloaded the latest updates for your wireless driver. Do note that you need to used a wired connection for this, if your wireless doesn't work out of the box.

As for some cards being restricted, this is the first I've heard of that. Your chipset at least is well supported, Broadcom released a native Linux driver (the STA) for it last December.

---

### Post by adok on 2009-09-18
I have the same wireless card, and there wasnt any problem in making it work after install b43-fwcutter.

---

