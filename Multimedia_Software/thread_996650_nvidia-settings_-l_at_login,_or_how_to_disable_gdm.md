---
title: "nvidia-settings -l at login, or how to disable gdm?"
date: 2008-11-29
forum: Multimedia Software
---

### Post by Cowloon on 2008-11-29
So, none of the suggestions that I've read fix the problem for me where my display resolution is at 1280x1024 once I login. I can run nvidia-settings and change the resolution to 1600x1200, save and merge and it does nothing since my xorg.conf is already set to use 1600x1200 resolution instead of 1280x1024.

I've noticed that the refresh rate visibly changes as soon as gdm selects a window manager for me to login with. So, I tried killing gdm and running startx to launch my window manager. I find that if I add nvidia-settings -l to .xinitrc, then I can run startx and my window manager launches and my screen resolution is set to 1600x1200.

I tried adding this to .xsession and restarting gdm, but it goes back to the same behavior.

So, I would actually prefer to start X by running startx, than to have gdm running, and this would also fix the display resolution problem, apparently. But, dpkg, or whatever, wants to uninstall ubuntu-desktop if I try to uninstall gdm. Should I modify my /etc/init.d/gdm to disable gdm, or is there a better way to do that?

---

### Post by evildragon2 on 2008-11-29
Nvidia settings changes what resolutions are availiable and temporarily applies them. To change permanently go to System->Preferences->Screen Resolution to apply your modifications.

---

### Post by doas777 on 2008-11-29
I had somthing simmilar goiing, and had to also set the gdm screen resolution app to the same value as the nvidia-settings config, before i could get it to work. I think the merge failure has somthing to do with the new configless xorg. 

the nvidia-settings -l also fixes my tv-outs overscan, so it was a beneficial thing anyway. I just wish it didn't have to load the window at login.

have fun

---

### Post by Cowloon on 2008-11-29
If I run nvidia-settings and then use Screen->Preferences-Screen Resolution in gnome, it doesn't give me the option to select the refresh rate I have. Selecting 85hz in nvidia-settings, in the gnome app, the first time it wanted to offer 135hz, which scared me. The next time it only offers up to 54hz.

Besides that, this doesn't really seem to be the right path to look down, because I have this behavior regardless if I use wmii, i.e. I fix the resolution/refresh rate in nvidia-settings. save and merge, log out, log back in and I'm back to the low screen resolution/refresh rate.

I also tried using the option to use my x scripts, and verified that .xession is being run, but for some reason it still doesn't fix the screen resolution problem.

So, I've editted /etc/init.d/gdm to exit immediately. Now, I can run startx and it uses the correct screen resolution/refresh rate.

I think this indicates that this issue with screen resolution not sticking, is not an nvidia problem, it's a gdm problem.

---

### Post by Cowloon on 2008-11-30
So, I noticed the file:

/etc/X11/Xsession.d/40guidance-displayconfig_restore

that runs displayconfig-restore, which resets your screen resolution! So, I commented out the call to displayconfig-restore, e.g.:

#/usr/bin/displayconfig-restore || true
true

and now I can run gdm and not have my screen resolution reset.

---

