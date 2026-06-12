---
title: "Latest Kernel Upgrade and nVidia Kernel Module Version Mismatch"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by diepruis on 2007-09-26
Hi,

this morning I downloaded the new kernel upgrade, rebooted and reinstalled the proprietary nVidia driver. All was well, until I had to reboot again and X choked with a complaint that the nVidia kernel module's version doesn't match the driver's.

By the way, this is driver 100.14.19, installed from the file distributed by nVidia from their website.

Since then, I've tried uninstalling and reinstalling the driver, installing only the kernel module and everything else I could think of. Every time I reinstall, the driver works fine until I restart. Anyone have an idea what's going wrong here?

---

### Post by bluelaguna on 2007-10-13
I think I was having a similar problem.  After searching around, it seems there was this bug with the restricted modules deb.

Try:

```
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```

This is due to the bug found here:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217)

---

### Post by diepruis on 2007-10-14
> **bluelaguna said:**
> I think I was having a similar problem.  After searching around, it seems there was this bug with the restricted modules deb.

Try:

```
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```

This is due to the bug found here:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217)

This file did not exist for me, so the solution does not apply.

I attached my x.org error log for more information.

---

### Post by shinaab on 2007-10-17
I wish I had something positive to contribute to this thread but I am experiencing the same problem. I've spent the last several hours of my waking life searching the net and trying to solve this problem with no luck. There has to be someone out there with the solution.

---

### Post by diepruis on 2007-10-18
> **shinaab said:**
> I wish I had something positive to contribute to this thread but I am experiencing the same problem. I've spent the last several hours of my waking life searching the net and trying to solve this problem with no luck. There has to be someone out there with the solution.

Hey that's at least a start. At the least we know it's not just me being stupid now. Now either something is broken or both of us are being stupid!

---

