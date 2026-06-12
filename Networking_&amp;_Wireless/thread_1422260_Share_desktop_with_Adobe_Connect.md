---
title: "Share desktop with Adobe Connect?"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by r-senior on 2010-03-05
OK, some brief background ...

I deliver training courses for a big training company who are implementing a system to offer courses to a mixture of in-class and remote attendees. The virtual classroom is developed using Adobe Connect and works very well.

I usually show additional examples and code using my own Ubuntu laptop and with a traditional classroom this has just meant plugging a VGA cable into a VGA switch box and showing it through the projectors. With the virtual classroom the course demo machine has its desktop shared (simple display only, no remote control, no VoIP, etc) through Adobe Connect so that it is visible in class and to remote attendees. I would like to do the same with my laptop (a) because Ubuntu is my preferred desktop and (b) I like to show that a free O/S and tools are viable alternatives.

However ... despite setting up remote desktop and validating that with a VNC client, Adobe Connect doesn't offer the option to share my Ubuntu desktop. Despite not being officially supported, the Adobe Connect plugin appears to work OK through Ubuntu/Firefox in other respects.

The only solution I've found (in someone's blog) is to run TightVNC in a Windows VM, connect it to show the Ubuntu desktop and share the Windows VM desktop with TightVNC running fullscreen. Clever but not elegant. I suppose I could do similar with VNC from the course demo PC to my laptop without using a VM.

Does anyone have any clearer idea what the underlying issues might be with Adobe Connect and the Ubuntu Desktop? Other than "Adobe don't support it".

---

