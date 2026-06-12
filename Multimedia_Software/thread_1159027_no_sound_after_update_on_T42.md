---
title: "no sound after update on T42"
date: 2009-05-14
forum: Multimedia Software
---

### Post by redtuna29 on 2009-05-14
After I updated to Ubuntu 9 from 8.10, my sound controls don't work. Specifically, no sound controls (up, down, mute), no acpi event for sound controls, no notification for sound controls or brightness. My sound does work manually in the volume control dialog. 

I'm guessing this is an acpi hotkey problem. Typing this:
echo enable,0xffffffff | sudo tee /proc/acpi/ibm/hotkey
into the terminal fixes all the problems. But I would like a permanent fix.

Any suggestions?

---

### Post by Stochastic on 2009-05-15
Moved to Multimedia & Video.

---

