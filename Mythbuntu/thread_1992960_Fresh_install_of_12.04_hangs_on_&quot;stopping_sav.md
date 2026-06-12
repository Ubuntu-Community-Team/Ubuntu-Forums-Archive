---
title: "Fresh install of 12.04 hangs on &quot;stopping save kernel messages&quot;"
date: 2012-06-01
forum: Mythbuntu
---

### Post by dthacker on 2012-06-01
Dell Optiplex 
Haupagge PVR 250 

Fresh install of 12.04 hangs at "stopping save kernel messages" and will not go further.   Googling finds posts that have had in install a different desktop manager, but I am not getting far enough into install to run apt.

Please advise.   Thanks for helping!

Dave

---

### Post by Kr0nZ on 2012-06-01
> When selecting the "Install Mythbuntu" option from the CD, the boot process hangs. The last message displayed on the console is "Stopping Kernel Save Messages". What do I need to change to get past this?

What happens when you boot into the live disk then try installing AFTER its booted? Are you using CD or USB?

I have never had success with installing from the boot menu.

---

### Post by superm1 on 2012-06-04
> **dthacker said:**
> Dell Optiplex 
Haupagge PVR 250 

Fresh install of 12.04 hangs at "stopping save kernel messages" and will not go further.   Googling finds posts that have had in install a different desktop manager, but I am not getting far enough into install to run apt.

Please advise.   Thanks for helping!

Dave

This is pre or post install (eg live disk?)  If it's post install, did you enable nvidia drivers?  If so, try with them disabled.  If it's pre-install, try with safe graphics mode in the live disk boot menu.

---

### Post by dthacker on 2012-06-07
Thanks for your replies.   This behavior happens [LIST]
[*]when I boot to the live CD
[*]When I access the boot menu and select install instead of "Try Mythbuntu"
[*]When I try to install Xubuntu 12.04 instead of Mythbuntu
[/LIST]

I am never able to boot successfully to an install CD.  MD5 Checksums are ok.  

Dave

---

