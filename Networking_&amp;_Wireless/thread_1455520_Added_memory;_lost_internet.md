---
title: "Added memory; lost internet"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by DavidChandler on 2010-04-16
I added RAM to my Acer (dual boot Windows XP / Ubuntu 9.1).  Windows continues to work.  Ubunty will no longer recognize the internet connection.  I don't know if adding the memory is what did it, but I am puzzled why I can use the ethernet card from Windows but no longer from Ubuntu.

---

### Post by Silent Warrior on 2010-04-16
Adding RAM has no business causing that. You didn't run any updates before this surgery, like updating the kernel or any modules-package?

---

### Post by DavidChandler on 2010-04-17
I didn't see how adding RAM could cause this problem.  I still have internet access through Windows, which I am using now.  How might one inadvertantly lose internet access?  It was set up automatically when I installed Ubuntu.  Is there some way to run the routines that are used at install time to re-initiate recognition of the ethernet card or whatever else might be needed?  Will updating to the new Ubuntu at the end of the month take care of the problem?  It would still be nice to learn how to solve this thing intentionally, without black magic.

By the way, how do you set up this forum so responses are automatically sent to my email?  I didn't find this response until I intentionally logged back in.

---

### Post by DavidChandler on 2010-04-17
> **Silent Warrior said:**
> Adding RAM has no business causing that. You didn't run any updates before this surgery, like updating the kernel or any modules-package?

I don't remember doing any upgrades, but sometimes I just click OK and let it upgrade when advised.  How would I see my upgrade history?

---

### Post by nitstorm on 2010-04-17
> By the way, how do you set up this forum so responses are automatically sent to my email? I didn't find this response until I intentionally logged back in.   	

Use Thread Tools-> Subscribe to this thread. Opens up a new page, select "instant notification by e-mail"

---

### Post by DavidChandler on 2010-04-18
I have dual boot with Windows and Karmic on separate hard drives.  Both were working, but now internet access is lost for Karmic.  This event coincided with installing extra RAM, but I don't see how that could cause internet access to be lost for Ubuntu and not Windows.

I don't know how to trouble shoot this problem.  Is there any way to re-run the setup routine from when I installed Ubuntu?

---

### Post by dineshs on 2010-04-18
ADSL ,dialup or mobile broadband...?
Pl post the output for 
```
ifconfig -a
```
Also check whether your ethernet is disabled by rightclicking on the network manager applet on right top

---

### Post by Iowan on 2010-04-18
Merged threads.

---

