---
title: "ASUS P4P800 mobo - Marvell Yukon Gigabit - skge vs sk98lin"
date: 2006-01-24
forum: Networking &amp; Wireless
---

### Post by Remillard on 2006-01-24
Hello,

I'm looking for advice and hoping someone out there has gotten Ubuntu running on a Asus P4P800-E motherboard.  The onboard Ethernet is a Marvell Yukon Gigabit Ethernet chip and it's not behaving itself under Ubuntu.  Under Gentoo, the newer "skge" driver seems to be working fine, however while Ubuntu correctly chooses skge, it doesn't work.  I've tried downgrading to the sk98lin driver, but either I'm not doing something right, or it's not the right thing to do, as it doesn't create a eth0 port.

Has anyone gotten this combination to work correctly before?

Best regards,
Remillard

---

### Post by awahl on 2006-01-24
Hi Remillard - I have ran Ubuntu 5.10 on my P4P800E-Deluxe with no problems via the Live CD. Haven't actually installed it on this particular machine (although I have 5.10 running on 2 others). Everything worked out of the box, including gigabit lan, but not @ gigabit speed....I did just order the D-Link G-520 from Newegg. Can't wait to try that.

Anyway - I can report no problems. But....it was the Live CD..I don't think that should matter. 

Cheers & good luck!

---

### Post by Remillard on 2006-01-24
Thanks for the information.  I went and tried the Live CD and it's still no joy.

There's nothing remarkable about the motherboard as far as I know.  I might try taking out the wireless card I suppose and see if that helps.  I did remove the wireless drivers and remove and reinstall skge and tried it, and then tried sk98lin, and no joy either.

---

### Post by Remillard on 2006-01-27
Just thought I would give this thread a bump.  I'm considering that the only thing to do is to put a linux kernel source onto a flash drive and try to recompile the kernel and see if a more recent kernel version will handle the skge and sk98lin drivers better.

---

### Post by Sn4ke on 2006-01-31
I don't know if this can hel you but have you tried booting with the 

acpi=off

option?

With live edition before booting:
**live acpi=off**

if don't work try: noapic nolapic acpi=noirq (or acpi=off)

---

### Post by Clefferson on 2006-03-22
Pehaps it can help you having a look... [here]("http://ubuntuforums.org/showthread.php?t=112626&highlight=asus+p4p800+solved")!

---

### Post by cabomix on 2006-08-25
I have no experience with you mobo, but ASUS usually enables and desables integrated devices from bios, check it and if it is active do a hard bios reset and reconfigure. Chances are that is the root of your troubles. Other wise your mobo may need a trip to ASUS. Best of luck.(Personal experience with ASUS talking here;))

---

### Post by Remillard on 2006-08-25
The problem completely disappeared with Dapper.  I think it was a driver issue in the Breezy kernel.

---

