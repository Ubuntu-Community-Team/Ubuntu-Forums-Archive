---
title: "dvd ram can't be recorded to..."
date: 2008-03-30
forum: Mythbuntu
---

### Post by Scott Atkinson on 2008-03-30
Having mangled the English language for a title...

I have an LG external dvd burner that functions beautifully under Mythbuntu, except for the dvd ram part.

I tried to record something to dvd ram today, but Serpentine didn't see the disc as recordable.

After a search or two, I ended up modifying /etc/fstab to include 'rw' in the relevant line.

I also installed udftools.

When I tried to format a disc, it very quickly returned a description of the disc's structure - so I'm guessing it was already formatted. Besides, it shows on my desktop as a udf disc.

Serpentine continued to not work, so I guessed it was simply an application that doesn't support dvd-ram. I downloaded Brasero, which recognised the dvd-ram disc but wouldn't burn, complaining that it lacked the right plug-ins.

I have no idea what such a plug-in would be, or what else I'm doing wrong.

Thanks,

Scott A.

---

### Post by okey666 on 2008-04-30
I have the same problem

---

