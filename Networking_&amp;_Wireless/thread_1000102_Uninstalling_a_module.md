---
title: "Uninstalling a module"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by andreasis on 2008-12-02
BACKGROUND:

I have installed the rt2570 wireless driver module on my intrepid system.
It didn't work like it did in hardy, so I'm switching back to the driver that came with intrepid, which works just fine.
I have blacklisted the driver in /etc/modprobe.d/blacklist and the system reverted back to the original driver without a problem.

QUESTION:

Who can tell me how to uninstall/completely remove rt2570 from the system?

If I unblacklist the rt2570 driver and blacklist the original, rt2570 is implemented upon reboot, so I know that it is still there.
sudo make uninstall does not work/is not applicable.

THANK YOU

to anyone for your help.

---

### Post by cariboo on 2008-12-02
You can't completely remove the module, as it is part of the kernel, just leave it blacklisted and it won't load again. 

If you really want to remove the module, if you still have the source directory you should be able to run make uninstall from the source directory.

Jim

---

