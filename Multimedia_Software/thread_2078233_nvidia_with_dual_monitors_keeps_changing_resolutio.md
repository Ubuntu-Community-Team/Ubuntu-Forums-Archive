---
title: "nvidia with dual monitors keeps changing resolution"
date: 2012-10-30
forum: Multimedia Software
---

### Post by Cammy on 2012-10-30
I have an nvidia 9500GT and am using the drivers that shipped with 12.10 (304.43).  I'm running two 19" monitors, and the left one is on a KVM switch that I can toggle between my ubuntu machine and a Win7 machine.

In nvidia-settings, under X Server Display Configuration, I have Twinview set up, with the left monitor being my primary and am running 1280x1024 on each monitor.

**My problem:** When I'm switched over to the Win7 machine on the KVM switch, something seems to happen that causes the resolution on the left monitor to drop down to 1280x1024.

I can solve this temporarily by going into nvidia settings, then to X Server XVideo Settings, and telling the machine to  sync to the right monitor, but it won't seem to save that setting through a reboot (and sometimes before I even reboot).  In fact, no matter what I do in nvidia-settings, most of my settings are lost after a reboot, despite me saving them to a file. 

If I set my resolution to 1280x1024, it resets to auto.
If I change which monitor to sync to, it changes it back.
If I pick the other monitor as my primary monitor, it changes that back too.

Is there a way to make nvidia-settings save my settings, or some way to make it honor my desired resolution?

---

### Post by Milambar on 2012-10-30
Yes,

Stop using windows.

---

### Post by Cammy on 2012-10-30
I'll remember that the next time you want to play Red Alert 2. :p

---

### Post by papibe on 2012-10-30
Hi Cammy.

Try saving your current setup using 'Nvidia X Server Settings' (nvidia-settings).

First save your current xorg.conf, just in case:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Then run nvidia-settings as root:
```
gksudo nvidia-settings
```
Once open click on 'X Server Display Configuration' at the left. Set resolutions and other settings as you need it. Once you are happy with the configuration, save the settings by pressing 'Save to X Configuration File'.

Restart to check if the settings were set correctly. In case you run into problems, recover your old settings by doing:
```
sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf
```
I hope it helps, and tell us how it goes.
Regards.

---

### Post by Cammy on 2012-10-30
Thanks papibe!

I've previously tried saving the settings to /etc/X11/xorg.conf (there wasn't one of those files originally) but it all seems to reset the first time the screen cycles off when switched over on the KVM.

At first I thought this was my wallpaper changer, so I changed the frequency to 24 hrs, but it still happens.  Then I thought it was from the screen automatically turning itself off after an hour of non-use, but I've seen the resolution switch while the screens are still on.

There's something that's causing ubuntu to change my screen resolution on my left monitor while I'm switched over on KVM, despite what xorg.conf says, and I have no idea what it is.

---

### Post by papibe on 2012-10-30
I see.

I would try first if adding 'nomodeset' to grub resolves the problem.

If that doesn't work, try this:
[LIST]
[*]Connect the monitor directly to the Ubuntu machine.
[*]Obtain the EDID data from the monitor.
[*]Hardcode the EDID file into the xorg.conf file.
[/LIST]
Let us know if you need help with any of that.
Regards.

---

### Post by Cammy on 2012-10-30
Awesome, thanks.  I've added that and we'll see if it works before I try the others.

Love your doggie avatar btw!

---

### Post by Cammy on 2012-10-31
> **papibe said:**
> I would try first if adding 'nomodeset' to grub resolves the problem.

This seems to have done the trick.  Thanks!

---

