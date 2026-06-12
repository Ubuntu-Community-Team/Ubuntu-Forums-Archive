---
title: "Todays Update Broken X"
date: 2008-10-15
forum: Multimedia Software
---

### Post by vbabiy on 2008-10-15
I have upgraded to 2.6.24-21-generic, and I am using nvidia-glx-new-envy and it broke X

Is there a fix for this.

---

### Post by wolfen69 on 2008-10-15
try
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot.

---

### Post by markbuntu on 2008-10-15
You need to remove the nvidia driver from envy and reinstall it.

---

### Post by wizardStan on 2008-10-15
I would greatly like to know what update it was that broke this, if anyone has the insight.  It took a disturbingly long time to get things back to normal and I'm hoping I at least gained something for the trouble.

---

### Post by markbuntu on 2008-10-15
If you have updated the proprietary driver from ati or nvidia, kernel updates can fail to load the driver kernel modules if you did not remove the previous driver. This is because more than one set of driver kernel modules is available so the new kernel does not know which one to install.

This is a very common problem and can be avoided by removing old proprietary drivers before installing new ones, even if you use envy this will happen.

---

### Post by wizardStan on 2008-10-15
I will take this under advisement, although I don't think it happened when I went from .16 to .19, but I may have simply forgotten it.
Thanks!

---

### Post by markbuntu on 2008-10-16
Most likely this did not happen with the -16 kernel or previous drivers because they were not using DKMS, which they are now.

EDIT: I just noticed that, along with missing release notes, installer notes are also not available yet. They have not updated their installer page for a very long time. Hopefully the new installer notes will include specific instructions for Ubuntu since they now claim to be providing installer support for Ubuntu in the last few drivers. We will just have to wait and see.

---

### Post by vbabiy on 2008-10-16
I had to go back to .19 because I tried to reinstall drives and it didn't help. I am on a Dell XPS m1530 with the Nvida Card

---

### Post by Stinger on 2008-10-16
> **wizardStan said:**
> I will take this under advisement, although I don't think it happened when I went from .16 to .19, but I may have simply forgotten it.
Thanks!

You are right, it didn't that was my experience too. I'm using EnvyNG to install the Nvidia driver, and to my knowlegde it's supported in ubuntu right ?



> **markbuntu said:**
> Most likely this did not happen with the -16 kernel or previous drivers because they were not using DKMS, which they are now.

You say that the new -21 kernel is using [DKMS]("http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support") ? Has there been any official announcement about the change ? I haven't seen any. 
8.04 is a long therm support release, I would have expected more testing before such dramatic change that leaves lots of users with non working drivers, that be non working X, audio, wireless and so on.

---

### Post by markbuntu on 2008-10-16
The problem with gpu drivers only occurs when there is more than one set of kernel modules available which happens quite often because people do not remove the old drivers and kernel modules when they update their drivers. I think envy also does this though it is hard to tell. 

If you have installed "unsupported" items like proprietary drivers and other stuff not from the repos then they may fail to work on kernel updates. This is the explicit statement of "unsupported".

The -21 kernel has been testing for quite a while. I have been using it from hardy proposed since July or August. There have been many updates since the first proposed update to -21. I think I am at -21.45 or something like that.

Anyway, no one is able to test everything on every piece of hardware out there. If you are concerned about your hardware, turn on hardy proposed and join lauchpad. The devs are very good at fixing things they find out about and the only way they find out is through Launchpad bug reports. They really do not have the time to troll the forums.

---

### Post by Stinger on 2008-10-16
> **markbuntu said:**
> If you are concerned about your hardware, turn on hardy proposed and join lauchpad. The devs are very good at fixing things they find out about and the only way they find out is through Launchpad bug reports.

I am a member of launchpad, watching the bug reports, and filing bugs if necessary.  

> **markbuntu said:**
>  They really do not have the time to troll the forums.
This remark I find unnecessary, but if it makes you feel better I guess it's ok.

---

### Post by markbuntu on 2008-10-16
> **Stinger said:**
> I am a member of launchpad, watching the bug reports, and filing bugs if necessary.  


OK, so why the complaint if you know so much about what's going on.

> 
This remark I find unnecessary, but if it makes you feel better I guess it's ok.

That was not aimed at you particularly, or personally. It was for the people who come here who don't realize this.

---

