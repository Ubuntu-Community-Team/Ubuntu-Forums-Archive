---
title: "OS hangs during startup"
date: 2012-04-18
forum: Mythbuntu
---

### Post by cgjrdl on 2012-04-18
Hi there.  I've just installed Mythbuntu 11.10 on a new machine I built and am having real difficulty getting the OS to load fully.  Initially, after the UEFI/BIOS screen, everything went to black.  I addressed this by inserting "nomodeset" into /etc/default/grub (and running 'update-grub').

Right now, a number of lines appear on the screen detailing the services being loaded and it normally hangs at '* checking battery state' and also the screen fades to a really dim level where I can barely read it.  The lines I can read include AppArmour, LDM, ACPI, apache2.  All of these services have started.  I should also mention that at this stage I can gain ssh access and execute commands from the shell.

Please excuse the noob status but I'm not sure what's the best information to provide to help figure this out.  I thought rather than randomly dump my log files into this post, I'd outline the issue and perhaps someone can identify what would be useful for me to get.

Finally, as a test, I installed Fedora 17 beta, just to see if I could get any OS to work.  This went fine and it did appear to be fully functional.

Thanks in advance for any help.

P.S.  I appreciate visual issues + new custom build may well point to the graphics card.  On that front, I'm running an AMD 3670k integrated CPU/GPU.  I guess while I'm at it:
- mb: Asrock Socket FM1 A75M Micro-Atx
- ram: Kingston HyperX Genesis DDR3 1600MHz CL9 8GB DIMM
- ssd: Crucial CT064M4SSD2 64GB

P.P.S. I have spent some time reading previous posts but apologies if I've missed anything obvious that addresses this.  Feel free to point me to it if so.

---

### Post by Ryan-M- on 2012-04-18
I had a similar issue on upgrade to 11.10 and myth 0.25.

My problem was a bit more random, sometime it would boot all the way to the desktop after a restart but never boot from a shutdown, each time it would hang at the "checking battery state"

I think its an issue with the change of desktop managers, lightdm to gdm along with the autostart that mythbuntu employs.

In short after messing with my graphics drivers for ages, I removed lightdm, installed gdm and removed its config file in /etc/gdm/custom.conf

Ryan

---

### Post by cgjrdl on 2012-04-18
Ok, thanks for the tip Ryan.  I'll do some tinkering and see what happens.

---

