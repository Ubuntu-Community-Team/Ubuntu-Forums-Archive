---
title: "Acer Atheros Wireless card not detected"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by jcb081584 on 2009-05-20
I have and Acer Aspire One with an Atheros network card (not sure which one) and lately I've been having problems getting it to see wireless networks.  I got it working for a few moments earlier this morning but after doing an update I had to reboot my computer and my card is  not even recognized with iwconfig at all.  The output of iwconfig is:

lo        no wireless extensions.

eth0      no wireless extensions.

virbr0    no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

I can recognize it in lspci -v the output of which is:

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Foxconn International, Inc. Device e008
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 55200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: ath_pci, ath5k

It has been recognized but now it's not.  Can anyone tell me how to get ubuntu to recognize and use it again please?  Thanks in advance.

---

### Post by jcb081584 on 2009-05-20
After doing a couple more commands I have noticed that the modules file in /proc is empty.  Can anyone tell me why this would be please?

---

### Post by superprash2003 on 2009-05-20
when you boot , in grub , choose an older kernel and see if wireless works agai

---

### Post by jcb081584 on 2009-05-21
> **superprash2003 said:**
> when you boot , in grub , choose an older kernel and see if wireless works agai

Negative. It still does not work.

---

