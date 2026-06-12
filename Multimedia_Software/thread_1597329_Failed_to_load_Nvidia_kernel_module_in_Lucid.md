---
title: "Failed to load Nvidia kernel module in Lucid"
date: 2010-10-15
forum: Multimedia Software
---

### Post by Wtwine on 2010-10-15
Hi

I am running my PC on Lucid.  It has been working fine, but suddenly the other day I got an error message when booting, saying that Nvidia kernel module failed to load. I had to boot in low graphics mode.  The only thing i can think of that had changed is that I had recently upgraded to latest Linux kernel 2.6.36-25.

I have tried carefully following tips on numerous threads on this forum and others, but still no go.  

I have purged nvidia drivers and reinstalled nvidia-current (also tried nvidia-glx-185).  However, when I then do <sudo modprobe nvidia>, I get this message:

WARNING: All config files need .conf: /etc/modprobe.d/lrm-vide, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/aliases, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/lrm-video, it will be ignored in a future release.
FATAL: Module nvidia not found.

When I go to System>Administration>Hardware Divers, it shows Nvidia-current as present but not currently activated.

I have blacklisted vga16fb and nouveau in blacklist.conf, done <sudo nvidia-xconfig> etc.

I am at a loss as what to do next, and am still new enough to Linux to not be in a position to fiddle to try fix it myself.

Any advice would be greatly appreciated!

Cheers

---

### Post by Wtwine on 2010-10-19
Problem solved.  It turns out that my GeForce4 T4200 graphics card  requires the Nvidia-glx-96.43.xx legacy driver, and is not supported by  the current driver (260.19.xx).  When I upgraded, the legacy driver must  somehow have been replaced by the current one.

So, I purged all installed nvidia drivers again (sudo apt-get --purge  remove nvidia*), installed Nvidia-glx-96 and associated recommended  packages in Synaptic, and rebooted.  Now my graphics card works again!   At last!

---

