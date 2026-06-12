---
title: "Ack! WG511(Prism54) card won't come up."
date: 2006-02-21
forum: Networking &amp; Wireless
---

### Post by jay_cee on 2006-02-21
HI - 

I can't get my Netgear WG511 card to work (no lights. Dead as a doornail). Its a V1 card that uses the prism54 driver (previously worked under Mandriva 10.1). I'm running Kubuntu 5.10 which claims to autoconfigure this card...but it didn't.

Here is what I have figured out thus far:

lspci returns:
Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)

iwconfig returns:
eth0      NOT READY! blah...blah...normal wireless information

(note that eth0 is my wireless card. So it is recognizing that the card is there, but somehow it is NOT READY!)


Inserting the card generates the following log messages:
ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
pci.agent[7104]:   prism54: already loaded

lsmod confirms that prism54 is in fact loaded. 

Now what I can't find in the log is any indication that the isl3890 firmware is getting loaded. In fact, when I looked in /usr/lib/hotplug/firmware, there was nothing in the directory. So I downloaded the firmware from prism54.org and placed it in that directory as isl3890. I had to do something similar in Mandriva. Still no joy. I suspect that the firmware is not getting loaded into the card, but I really don't understand this hotplug subsystem at all.

Any help/tips is much appreciated!
-J

---

### Post by Lambert on 2006-02-21
Not real familiar with this driver and firmware, but with the NOT READY part of iwconfig, I'm wondering if your radio is just switched off.

Do you have a button or key combo that turns on and off the wireless radio?

Sometimes the key bindings aren't set properly and it doesn't work so you might be able to find a manual way to do it. What model laptop are you using?

---

### Post by jay_cee on 2006-02-21
Hi - 

Its an old IBM thinkpad 600e. FWIW - I didn't have to do any sort of key sequence to turn it on under Mandriva.

-J

---

### Post by Lambert on 2006-02-21
You're correct, it won't have it and I was thinking minipci, so I was way off. sorry I can't offer any more.

---

### Post by 11hjpphty76lkjj on 2006-03-12
Any other luck with this?  I'm attempting to get the same card working. 

Thanks!

Aaron

---

