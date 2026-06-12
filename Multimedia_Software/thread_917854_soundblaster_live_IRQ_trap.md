---
title: "soundblaster live IRQ trap"
date: 2008-09-12
forum: Multimedia Software
---

### Post by trash on 2008-09-12
Ok before i throw this card in the garbage one last attempt to get it working. It's detected as Live and set with asoundconf set-default-Live.
As soon as i start playing a cd I get "IRQ trap at vector"...

If I disable onboard sound I get kernel panic lockups. I'm not familiar enough with bios to play around with the irq settings so does anybody have any ideas for me?

---

### Post by Darkhack on 2008-09-12
Sometimes APIC and ACPI can cause IRQ issues.  Try booting with...

noapic nolapic

and if that doesn't work then,

noapic nolapic acpi=off

---

### Post by trash on 2008-09-12
tried them all with the same results each time.:(

the last things i see in the logs are kinda wierd, ISOFS: changing to secondary root... unhandled IRQ's and spurious APIC interrupt on CPU(should never happen)... then a whole bunch of IRQ handle/unexpected IRQ traps.

---

