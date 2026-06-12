---
title: "Force console video mode Grub2 - no monitor"
date: 2010-03-23
forum: Multimedia Software
---

### Post by BillRebey on 2010-03-23
I have a very annoying problem, and I'd appreciate any help I can get.  

Background:  I run a number of Ubuntu 9.10 boxes attached to multiple daisy-chained KVMs.  None of the PCs are using any GUIs - they all run in console mode.  I often reboot them remotely via an SSH session, etc.  

Problem:  If a monitor isn't actually active on the PC when it reboots, Grub2 uses a low-res video mode, despite having the video mode set correctly in Grub2's configuration files.  

If I reboot WHILE THE MONITOR is attached to the Ubuntu PC via the KVM, the video mode is set correctly as configured in Grub2's config files.

If I reboot WITH NO MONITOR attached, the video mode is ignored and I'm stuck in a low-res mode next time I attach to the PC via the KVM.

How can I force Grub2 to honor the configured graphics setting, despite not having a monitor present at the time it boots?

Thanks for any help - this is a very aggravating problem.

(If there is a better forum on which to post this, please advise!)

---

