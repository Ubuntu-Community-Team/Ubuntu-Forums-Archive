---
title: "bypass auto login/ FSTAB issues"
date: 2010-08-31
forum: Mythbuntu
---

### Post by Chewiesw on 2010-08-31
How can I  bypass the auto login?

I have recently upgraded my Windows PC to Windows 7 and the shares have changed.  My fstab is wrong and I therefore get the following message “ my press s to skip mounting or M for manual recovery” when I try to boot into myhtbuntu. If I press S or M nothing happens. If I press escape, I get loads of text.

I have tried to ssh on to the box, but that doesn’t work. I need to get to a place where I can edit my fstab.

I would also like to know if using FSTAB is the best way to mount to shares and if so, how I can get fstab to bypass mounting a share if it can’t find it.

---

### Post by ian dobson on 2010-08-31
Hi,

Maybe boot is rescue mode (If you have grub2 shift key during bios to display the grub menu).

I always put my network mounts in /etc/rc.local as long as they're not required during the boot process. If the worst comes to the worst the share isn't there after booting but the system boots without any problems.

Regards
Ian Dobson

---

### Post by marshcast on 2010-11-27
> **ian dobson said:**
> Hi,

Maybe boot is rescue mode (If you have grub2 shift key during bios to display the grub menu).

I always put my network mounts in /etc/rc.local as long as they're not required during the boot process. If the worst comes to the worst the share isn't there after booting but the system boots without any problems.

Regards
Ian Dobson

thanks Ian :)

---

