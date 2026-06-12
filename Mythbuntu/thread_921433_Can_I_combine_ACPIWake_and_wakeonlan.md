---
title: "Can I combine ACPIWake and wakeonlan"
date: 2008-09-16
forum: Mythbuntu
---

### Post by volkswagner on 2008-09-16
When my master backend shuts down via mytthv ACPI wake command, I can't wake it via wakeonlan.

Is there anything I can add to the ACPI wake script to allow this?

---

### Post by volkswagner on 2008-10-07
Hmm, anyone?
What else shall I provide?

---

### Post by volkswagner on 2008-10-07
Well, I just ran an idiot test.  I passed.  I'm an idiot.  I'm not sure what the problem was in the past.  It worked using just the mac address, after an auto shutdown.

I guess ACPI wake and wakeonlan can live together in harmony.  I will run some more tests prior to marking as solved.  I would however like to hear from others on working systems, using both WOL and ACPI wake.

Cheers

---

### Post by laga on 2008-10-08
Mine works.

Back on 7.04, I had to make some tweaks to the init scripts to prevent them from shutting down the NIC. I'm not sure if that's still needed in 8.04.

---

