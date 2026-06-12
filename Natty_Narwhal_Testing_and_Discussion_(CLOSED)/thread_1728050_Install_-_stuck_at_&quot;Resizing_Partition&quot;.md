---
title: "Install - stuck at &quot;Resizing Partition&quot;"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ubanksy on 2011-04-13
Installing the latest Beta off a DVD onto a Presario CQ60 laptop (friend's slow machine with 160GB HDD) alongside Vista (150GB) and a hidden recovery partition (10GB) - both detected by the installer.

Told the installer to install alongside existing OS (although I did look inside the advanced partition tool) and it defaulted to 40GB for Ubuntu - so would have to shrink the NTFS from 150GB to 110GB.  HDD light went to fully on and it appeared to be resizing, so I left it.  Back now after an hour or so, and screen still says Resizing Partition, but HDD light is not on.

Ctrl-Alt-F2 and top don't tell me anything (appears to be idle), sudo fdisk -l reports: 

/dev/sda1 
/dev/sda2

dmesg doesn't have anything obviously interesting to me - some drm:drm_mode_getfb *ERROR* invalid framebuffer id entries but that's it.

Ctrl-Alt-F7 and the gnome window for the installer is now blank, and the spinning wheel is still there.  Is there any way I can check on the health of the installer (log or similar)?

Or any suggestions for next steps - would like to complete the install.

I'm not convinced this is Natty related, the machine was running pretty slowly prior to this - hence wanted to trial ubuntu alongside vista to see if the OS was to blame.

---

### Post by psusi on 2011-04-13
Oh boy, that's not good.  Are you sure there are no disk related errors in dmesg?

---

### Post by cubeist on 2011-04-13
Looks like it has been a few hours, but it still might not be a concern.  I once did a windows partitions resize that took about 8 hours!

If you quit the procedure you may never recover your windows partition!  I would leave it awhile longer.  Post back, keep us updated.

---

### Post by kansasnoob on 2011-04-13
Quite possibly this very old bug:

[https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/19732](https://bugs.launchpad.net/ubuntu/+source/partman-partitioning/+bug/19732)

I suggest creating the partitions ahead of time and then just installing to them as described here:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by ubanksy on 2011-04-13
It's been 10 hours and no change from before - installer is definately hung.  Nothing new in dmesg either.  Not sure if I should have done a hdd health check prior to starting (which one?)

Based on that fdisk, the only partitions are the Vista and the hidden recovery one.

What would you do next?

EDIT: As suggested, I rebooted into Windows, which ran a repair successfully.  I then did partitioning via Live CD, and installed into the gap between Vista and the recovery image.  System has been running fine for 3 weeks.  Grub2 displays all 3 options.  Performance difference between Vista and Ubuntu has to be seen to be believed - that Windows install is truly borked - Ubuntu flies.

---

### Post by cubeist on 2011-04-13
> **ubanksy said:**
> It's been 10 hours and no change from before - installer is definately hung.  Nothing new in dmesg either.  Not sure if I should have done a hdd health check prior to starting (which one?)

Based on that fdisk, the only partitions are the Vista and the hidden recovery one.

What would you do next?

at ten hours I would say it's definitely dead.  Boot back into your windows side (might have to boot into safe mode and do repairs) then resize the partition from within windows (lots of tutorials available).

Also, if you don't have a recent backup of your entire system you may want to take the time and save all your personal data!

---

