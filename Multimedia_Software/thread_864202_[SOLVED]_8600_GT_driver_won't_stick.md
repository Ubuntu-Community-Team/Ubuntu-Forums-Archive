---
title: "[SOLVED] 8600 GT driver won't stick"
date: 2008-07-19
forum: Multimedia Software
---

### Post by drewcoon on 2008-07-19
Hello!

I've recently built a computer rig with Ubuntu on it, and I'm having trouble with getting my nVidia drivers for my 8600 GT to work properly.

If I ctrl-alt-f3 to a terminal, killall gdm, then uninstall and reinstall the nVidia drivers (via the driver installer off their site), then start gdm, The driver works flawlessly. However, next time I start up the computer it is running in low graphics mode and I have to repeat the previous procedure to make it work again.

I've run nvidia-xconfig to update my xorg.conf as well... Why won't my driver kick in automatically when I start up? Can anyone help me? Thanks in advance :)

---

### Post by overdrank on 2008-07-19
> **drewcoon said:**
> Hello!

I've recently built a computer rig with Ubuntu on it, and I'm having trouble with getting my nVidia drivers for my 8600 GT to work properly.

If I ctrl-alt-f3 to a terminal, killall gdm, then uninstall and reinstall the nVidia drivers (via the driver installer off their site), then start gdm, The driver works flawlessly. However, next time I start up the computer it is running in low graphics mode and I have to repeat the previous procedure to make it work again.

I've run nvidia-xconfig to update my xorg.conf as well... Why won't my driver kick in automatically when I start up? Can anyone help me? Thanks in advance :)

Hi and you may try what PmDematagoda suggested in a earlier thread
Do this:-
1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"

and save the file.

Then reboot the PC and see if the Nvidia driver now works.
[http://ubuntuforums.org/showthread.php?t=795997](http://ubuntuforums.org/showthread.php?t=795997)

---

### Post by drewcoon on 2008-07-19
THANKS! I rebooted and the driver is still working.

I'mma go thank PmDematagoda as well... Thanks again :)

---

