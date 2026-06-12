---
title: "Tip - Fixing incorrect nouveau resolution by deleting xorg.conf"
date: 2011-02-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cmccauley on 2011-02-15
Hi,

I upgraded yesterday via 'update-manager -d'. Unfortunately when the system restarted the nouveau driver limited my resolution to 800x600. Eventually I discovered that deleting the xorg.conf (actually moving it out of the way) and restarting allowed the correct resolution 1920x1200 to be detected.

Along the way, I tried switching to the latest nvidia drivers but that caused the system to hang on boot at 'Checking Battery State'.

Hopefully that helps someone else

Chris

---

### Post by cariboo on 2011-02-15
The nouveau driver doesn't need an /etc/X11/xorg.conf.

---

### Post by ronacc on 2011-02-15
it may not need one but when installed with additional drivers one is written and interestingly it specifies "vesa" as the driver ? I checked my /etc/x11/ just before and just after installing nouveau so I'm quite sure where the xorg.conf came from . Note ! on reboot after installation I had the correct res (1920x1200).

---

### Post by Harry33 on 2011-02-15
> **ronacc said:**
> it may not need one but when installed with additional drivers one is written and interestingly it specifies "vesa" as the driver ? I checked my /etc/x11/ just before and just after installing nouveau so I'm quite sure where the xorg.conf came from . Note ! on reboot after installation I had the correct res (1920x1200).

Now that is interesting.
Usually vesa belongs to the failsafe xorg (=xorg.conf.failsafe).

---

### Post by ronacc on 2011-02-15
> **Harry33 said:**
> Now that is interesting.
Usually vesa belongs to the failsafe xorg (=xorg.conf.failsafe).

I thought it was rather interesting also , I had been playing around with the 270.26 nvidia driver and after I un-installed it I checked to make sure that the xorg.conf was gone after installing nouveau I checked again to see if it had written one and it was there but specified vesa ?

---

### Post by cmccauley on 2011-02-16
> **cariboo907 said:**
> The nouveau driver doesn't need an /etc/X11/xorg.conf.

The point isn't whether not it needs one but rather that having one can cause problems. Having an old one in place caused the resolution to drop to 800x600. Removing it and rebooting resulted in the correct resolution.

---

### Post by Harry33 on 2011-02-16
> **ronacc said:**
> I thought it was rather interesting also , I had been playing around with the 270.26 nvidia driver and after I un-installed it I checked to make sure that the xorg.conf was gone after installing nouveau I checked again to see if it had written one and it was there but specified vesa ?

Did you also delete the file, which blacklists nouveau?
See /etc/modprobe.d/nvidia-graphics-drivers.conf or something like that.
That is created automatically when installing nvidia-current.

---

