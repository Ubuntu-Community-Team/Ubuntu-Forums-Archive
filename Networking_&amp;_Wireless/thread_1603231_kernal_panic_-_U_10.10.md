---
title: "kernal panic - U 10.10"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by SriNarayanan on 2010-10-22
My system goes into kernal panic and doing some search on the forum got me this.
1.It could be wireless driver bug
2.It it is exposed when some one nearby switches on a n/g wifi router that triggers the bug 
and hence can occur at complete random ness 


Now I just want to know ,how to get the log information of the n/g router present around,
How do I get more log info to debug this issue.

The actual thread is locked , so just reposting everything
--------------------------------------------------------------------------------------------------------------------------------
 Ubuntu Forums      

Ubuntu Forums ([http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php))
-   x86 64-bit Users ([http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343))
-   -   [ubuntu] Freezes + Flashing Caps Lock ([http://ubuntuforums.org/showthread.php?t=999833](http://ubuntuforums.org/showthread.php?t=999833))

koolcracker     December 2nd, 2008 09:52 AM
Freezes + Flashing Caps Lock
 
Okay, so I've looked around a bit, but had some trouble. I've been using Ubunutu for probably 4 months on this computer and then suddenly yesterday Ubuntu started these random freezes where nothing would unlock it, the only thing I could do was a hard computer restart. The only thing that happens is my laptop caps lock LED flashes at a constant rate.

In case it was something I changed by accident, I did a fresh install of Ubuntu, and its still doing it! I haven't tested my windows yet, but do you think this could be a new hardware problem? Or does anyone know of a solution to this problem or a way to better diagnose it? I am struggling here haha, and any and all help would be greatly appreciated.

iponeverything     December 2nd, 2008 10:04 AM
Re: Freezes + Flashing Caps Lock
 
Quote:
Originally Posted by koolcracker (Post 6294104)
Okay, so I've looked around a bit, but had some trouble. I've been using Ubunutu for probably 4 months on this computer and then suddenly yesterday Ubuntu started these random freezes where nothing would unlock it, the only thing I could do was a hard computer restart. The only thing that happens is my laptop caps lock LED flashes at a constant rate.

In case it was something I changed by accident, I did a fresh install of Ubuntu, and its still doing it! I haven't tested my windows yet, but do you think this could be a new hardware problem? Or does anyone know of a solution to this problem or a way to better diagnose it? I am struggling here haha, and any and all help would be greatly appreciated.
The flashing caps lock is a kernel panic. When you did the fresh install, did you do the updates right away. The reason that I am asking is that problem may have been introduced in the latest update.

kep1616     December 2nd, 2008 10:04 AM
Re: Freezes + Flashing Caps Lock
 
My laptop (Toshiba Satellite u405) is also suffering from identical symptoms. I have been trying to debug it, but I am still new to Linux. The best I can figure is that there seems to be a correlation between the lockups and Openoffice, though it only started today so I cannot be sure.

Koolcracker, what hardware are you running Ubuntu on, and what programs are you running when it freezes?

Hopefully we can get someone to help us out here.

Edit:

I updated the kernel a few days ago. The problem started today. Also, booting the other kernels did not help the problem.

koolcracker     December 2nd, 2008 10:26 AM
Re: Freezes + Flashing Caps Lock
 
I did some extra hunting around after I posted and I think I found the solution to my problem anyways, I'll share it, see if you have the same.

I run an Intel 4965 wireless card, and apparently in the new kernal update 2.6.27 there is a bug. I found this in the release notes for Intrepid:

Quote:
System lock-ups with Intel 4965 wireless

The version of the iwlagn wireless driver for Intel 4965 wireless chipsets included in Linux kernel version 2.6.27 causes kernel panics when used with 802.11n or 802.11g networks. Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug. (Because the known fix requires a new version of the driver, it is not expected to be possible to include this fix in the main kernel package.)
So for now I have just disabled my wireless Internet, and after I completely update my system with all of the new packages I lost in my reinstall, I am going to install the backports. I guess that I had never picked up an n or g signal since installing intrepid a month ago, and I'm assuming that just yesterday someone installed one within range of my computer.

So this is what I found for my solution, I hope it can help you too.


All times are GMT -5. The time now is 11:32 AM.     

vBulletin ©2000 - 2010, Jelsoft Enterprises Ltd. Ubuntu Logo, Ubuntu and Canonical © Canonical Ltd. Tango Icons © Tango Desktop Project.

---

### Post by RJARRRPCGP on 2010-10-22
It could be motherboard and CPU interference.

---

### Post by SriNarayanan on 2010-10-22
> **RJARRRPCGP said:**
> It could be motherboard and CPU interference.

i doubt it is not hardware . The dual booted windows 7 runs perfectly .   And its completely random . And i updated with compat wireless driver to fix the negative channer number bug for aircrack  . So I suspect a bug that i introduced during update , or the bug may already be in the kernel and it gets exposed when some one close switches on a router .

---

### Post by SriNarayanan on 2010-10-23
How to debug kernal panic ?

---

