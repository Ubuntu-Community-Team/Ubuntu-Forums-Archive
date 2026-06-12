---
title: "Nvidia 8200m driver issues"
date: 2008-08-27
forum: Multimedia Software
---

### Post by VonKrunkovich on 2008-08-27
I have ZERO experience with Linux. I just installed Ubuntu 8.4 on my laptop tonight, and most everything is working properly except for two things. Number one, my video card was detected and drivers were installed, but once i restarted my computer it would begin to boot Ubuntu then the screen would turn off. After that i couldn't login until i repaired Ubuntu, and then it would be back to the default 640x480 resolution. Also my sound is very scratchy, and I'm really not sure why.

---

### Post by overdrank on 2008-08-27
> **VonKrunkovich said:**
> I have ZERO experience with Linux. I just installed Ubuntu 8.4 on my laptop tonight, and most everything is working properly except for two things. Number one, my video card was detected and drivers were installed, but once i restarted my computer it would begin to boot Ubuntu then the screen would turn off. After that i couldn't login until i repaired Ubuntu, and then it would be back to the default 640x480 resolution. Also my sound is very scratchy, and I'm really not sure why.

Hi and how did you repair, did you use the xfix option in recovery mode? You  can try what PmDematagoda suggest here after installing the drivers
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

```
Do this:-
1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Then reboot the PC and see if the Nvidia driver now works.
```

Edit
Thread closed duplicate [[COLOR="DarkRed"]Here[/COLOR]](http://ubuntuforums.org/showthread.php?t=902164)
Please do not create multiple threads on the same issue.

---

