---
title: "dual core (apic) OR wakup alarm but not both"
date: 2011-09-20
forum: Mythbuntu
---

### Post by kuro_man on 2011-09-20
mb: asus m4a88t-m
os: mythbuntu 11.04 Myth 0.24
cpu: athlon x2 250 4ghz
ram: 2gb
gfx: asus en210 silent

I noticed that my machine was only running one core.  After some research I set the APCI APIC to [enabled] in the bios, and bingo! both cores up and running.
However, later I noticed scheduled recordings were missing.

I set an RTC alarm manually and ran shutdown and it didn't work.  I tried a few other bios setting and even flashed the bios to no avail.

Finally I set APCI APIC to [disable] and rtc alarm worked again, but I only have 1 core!

So, can I get RTC working with APIC or can I get dual core working without APIC - any help appreciated.

---

### Post by kuro_man on 2011-09-26
anyone?

---

