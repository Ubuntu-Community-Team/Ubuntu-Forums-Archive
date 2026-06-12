---
title: "Boot failure Mythbunto 10.04 64-bit"
date: 2010-10-14
forum: Mythbuntu
---

### Post by Macka01 on 2010-10-14
Hi everyone,

Turned on my Mythbox today and was greeted by a blank screen (after bios startup info), after a while some text appeared:

> 
mount: mounting /dev/disk/by-uuid/7ccf6200-6f65-4257-baea-9ba9d5868edc on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init.
No init found. Try passing init= bootary.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)


A week or 2 a go I had fschk report an error and after repair discovered an entire partition had been emptied (the partition containing all of the recordings)


My thinking is some sort of HDD corruption, however, perhaps someone out there has some idea as to what has gone wrong and why?

This is the second time I have had 10.04 fail on this machine, when I had 9.10 installed there where no such problems.

---

### Post by superm1 on 2010-10-14
> **Macka01 said:**
> Hi everyone,

Turned on my Mythbox today and was greeted by a blank screen (after bios startup info), after a while some text appeared:



A week or 2 a go I had fschk report an error and after repair discovered an entire partition had been emptied (the partition containing all of the recordings)


My thinking is some sort of HDD corruption, however, perhaps someone out there has some idea as to what has gone wrong and why?

This is the second time I have had 10.04 fail on this machine, when I had 9.10 installed there where no such problems.
Are you shutting down improperly?

If not, it could easily be a HDD starting to fail.  I would recommend checking the SMART status and/or running a tool like Hitachi DFT.

---

### Post by Macka01 on 2010-10-14
The system shuts its self down automatically when recording finishes, I would assume it is shutting down properly, as no one is cutting the power or resetting it.

Would these be appropriate tools for checking the SMART status?
[http://prefetch.net/articles/diskdrives.smart.html](http://prefetch.net/articles/diskdrives.smart.html)
[http://karuppuswamy.com/wordpress/2010/05/19/how-to-predict-hard-disk-failure-in-ubuntu-with-3-clicks/](http://karuppuswamy.com/wordpress/2010/05/19/how-to-predict-hard-disk-failure-in-ubuntu-with-3-clicks/)

Is there any way I can boot my system without a disk or is that out of the question?

If I do need a disk is there anything special I need to do?

---

### Post by superm1 on 2010-10-14
> **Macka01 said:**
> The system shuts its self down automatically when recording finishes, I would assume it is shutting down properly, as no one is cutting the power or resetting it.

Whether it's properly depends mostly upon how you've configured it to shutdown I suppose.

> 
Would these be appropriate tools for checking the SMART status?
[http://prefetch.net/articles/diskdrives.smart.html](http://prefetch.net/articles/diskdrives.smart.html)
[http://karuppuswamy.com/wordpress/2010/05/19/how-to-predict-hard-disk-failure-in-ubuntu-with-3-clicks/](http://karuppuswamy.com/wordpress/2010/05/19/how-to-predict-hard-disk-failure-in-ubuntu-with-3-clicks/)

Is there any way I can boot my system without a disk or is that out of the question?

If I do need a disk is there anything special I need to do?
That second one is a good one.  You can get it by installing 'gnome-disk-utility' on your install.

If it's not turning up anything too informative, you can burn hitachi DFT to a CD.  They've got an ISO here: [http://www.hitachigst.com/support/downloads/#DFT](http://www.hitachigst.com/support/downloads/#DFT)

Boot off it and it has a very thorough test it will do, non destructively.

---

### Post by Macka01 on 2010-10-14
> **superm1 said:**
> Whether it's properly depends mostly upon how you've configured it to shutdown I suppose.
I followed the MythBuntu shutdown guide. From memory it executes: sudo shutdown -P now


I just managed to boot from the mythbuntu install disk and got palimpsest installed (using the install command you suggested)

Got something interesting:
403 power cycles (since the 18/1/2010)
53 Bad sectors
Read error rate: Good
Start Stop Count: Good
Reallocated Sector Count: [COLOR=Red]**Warning**[/COLOR]
----->Normalised: 99
----->Worst: 99
----->Threshold: 36
----->Value: 49 sectors
...
Current Pending Sector Count: [COLOR=Red]**Warning**[/COLOR]
----->Normalised: 100
----->Worst: 100
----->Threshold: 0
----->Value: 4 sectors

Is there a way that I can save the entire list of details?

It's not immediately obvious - and multiple items can not be selected, nor can I copy the items individually.

I'll start downloading the ISO for Hitachi DFT but I won't be able to test until this evening. Do you think it is still worth the time or is the information above enough to indicate failure (or lack of)?

---

