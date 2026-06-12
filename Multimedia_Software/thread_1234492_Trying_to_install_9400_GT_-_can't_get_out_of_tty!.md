---
title: "Trying to install 9400 GT - can't get out of tty!"
date: 2009-08-07
forum: Multimedia Software
---

### Post by Fraoch on 2009-08-07
I'm trying to install a Sparkle (yeah, I know) nVidia 9400 GT.

I can get to the BIOS and the boot process, but it won't go into graphics mode and drops me to tty with the following error screen:

```

Starting up ...
Loading, please wait...
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/b56d4734-34cd-4f9c-a992-04f6043ee504) = dev(8.2)
kinit: trying to resume from /dev/disk/by-uuid/b56d4734-34cd-4f9c-a992-04f6043ee504
kinit: No resume image, doing normal boot ...

Ubuntu 9.04 Sauron tty1

Sauron login: _
```

And after this I can get into the serial console fine.  Everything seems to be working except graphics...

The "No resume image" message is odd, I am not resuming from memory, I'm doing a cold boot.

I installed my older video card and installed the "nvidia-glx-180" package, which indicates it supports the 9400 GT, but no change.

Do I have to install the proprietary nVidia drivers from their site?  And if so, how do I do it from the serial console?

Thanks in advance.

---

### Post by mikewhatever on 2009-08-08
Try reconfiguring xserver: sudo dpkg-reconfigure xserver-xorg.

I think the 'odd message' is the result of checking for a resume image in case you suspended to disk, which is perfectly normal.

---

### Post by Fraoch on 2009-08-08
Thanks for the reply!  I didn't actually have to go that far.  After installing the Ubuntu (not nVidia) nVidia drivers, a new System - Administration item appeared, "NVIDIA X Server Settings".  I clicked on it while still running my old ATI card (otherwise I wouldn't have seen it) and a dialog box popped up with a helpful suggestion - the driver was installed but not in use and it suggested typing

```
nvidia-xconfig
```

as root, then restarting X.

So I did, fully prepared for it not to work and ready to reconfigure xserver as you suggested, but it worked.

I got a full-screen nVidia splash screen just before the Ubuntu GUI.  There was a minor glitch with the screen being massively off-centre and panning around when I moved the pointer, but after playing around with the resolution settings it's working as before and looking just fine!

Thank you.

---

### Post by ratcheer on 2009-08-08
I'm not sure how to solve your problem, but I am using a Sparkle 9400 GT card with absolutely no problems. Maybe the latest nVidia driver would help. I am using 185.18.31, which can be downloaded from the nVidia web site.

Tim

---

### Post by Fraoch on 2009-08-08
Actually it's working fine.  I'll change the thread title to "Solved".

Thanks!

---

