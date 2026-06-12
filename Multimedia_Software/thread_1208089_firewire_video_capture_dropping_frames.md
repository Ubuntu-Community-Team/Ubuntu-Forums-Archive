---
title: "firewire video capture dropping frames"
date: 2009-07-08
forum: Multimedia Software
---

### Post by ncumming on 2009-07-08
I'm trying to capture dv video off my panasonic PV-GS320 but keep running into problems after a few seconds.  I've tried kino, running out of the terminal as a superuser to allow access to the raw1394 driver.  After a few seconds, it begins dropping frames, more and more until it drops more frames than it actually captures.

I've also tried dvgrab (also with superuser privileges) and get a buffer underrun error.  

I've tried different firewire ports on my computer - one via a dedicated firewire card i have installed and also a port on my sound card.  Both yield the same resort.  

I'm running a 2.6 GHz P4 with 3.2 GB of memory, so i don't think system resources are a problem.  My CPU never gets above 50%, and isn't particuarly peaking when the frame drops start.  (curiously, the system monitor seems to think i have 2 processors and i only have one - no idea why that would be)  I'm running 9.04/Jaunty.

Any ideas?

---

