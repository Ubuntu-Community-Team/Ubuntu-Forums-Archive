---
title: "Mounting a windows drive on an Ubuntu laptop (connected via an ethernet network)"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by stelladeli on 2013-08-08
Hi!
Scenario: I have an Ubuntu 12.10 laptop and I would like to mount/have access to a laptop in general or its C drive that uses Windows 7.
Am I able to do that? If so, how?

I've understood that I can use smbmount for that purpose but I'm a total noob. 

Thanks in advance for your time.

---

### Post by turtles on 2013-08-08
You have 2 laptops. one windows one Ubuntu. Are you wanting to access a network windows share folder on the running windows laptop?
Or to you want to access the entire ntfs filesystem with the windows not running?
For the latter I would recomend using a live cd or USB and boot the windows laptop with that then use the live cd to mount the ntfs drive.
You can then copy all the data you want or repair it from the live cd or usb.

---

### Post by stelladeli on 2013-08-08
Thank you very much, yes I'd like the latter and I believe a bootable usb or CD is the best solution.

---

### Post by turtles on 2013-08-08
I have repaired countless windows installs with system rescue cd here is a link to how you can mount ntfs from there:
[http://www.sysresccd.org/Sysresccd-manual-en_Mounting_an_NTFS_partition_with_full_Read-Write_support](http://www.sysresccd.org/Sysresccd-manual-en_Mounting_an_NTFS_partition_with_full_Read-Write_support)

---

### Post by Mark Phelps on 2013-08-08
turtles: That link talks about mounting a Windows partition on the local machine; the OP wants to mount a Windows partition from a different machine.

As to mounting the "C:" drive read/write -- BAD idea, really BAD idea.  Pretty much a guarantee to corrupt the Windows OS filesystem if you mount the "C:" drive as read/write.  IF you must mount it in Linux, then mount it read-only.

And finally, not only does the laptop have to be running to mount the "C:" drive, it also has to be NOT hibernated.  If you try to mount a hibernated filesystem, the mount attempt will fail.  If you "force" it, while that might work, it will invariably corrupt the Windows filesystem as a result.

---

### Post by stelladeli on 2013-08-15
Thank you Mark for your insight.

---

