---
title: "[SOLVED] Unable to display splash screen at bootup Ubuntu 7.10"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by lyndaj70 on 2007-11-04
Hello,

I recently did a clean install of a desktop with Gutsy 7,10.

This system has an integrated ATi video card, and initially on bootup and shutdown instead of seeing the splash screen the monitor would display "cannot display video mode = recommended video mode  1280X1024"

I did a bit of research, and the release notes said that the resolution may be incorrectly detected at bootup, and to edit the /etc/usplash.conf file.

When I went there, I discovered that the resolution had been detected correctly

[HTML]# Usplash configuration file
xres=1280
yres=1024[/HTML]

But I backed up the old file and changed the resolution to 800X600 at first and currently have it set at 1000X1000

With both resolutions, I get the splash screen at shutdown, but still have the error message on the monitor at boot with no splash screen...

Could it perhaps be detecting the refresh rate incorrectly?  How would I check this?

Any help would be appreciated....

thanks,
~Lynda

---

### Post by divague on 2007-11-04
i solved this installing startupmanager, with this app i got the bootsplash

---

### Post by lyndaj70 on 2007-11-04
That worked!  
:guitar:

I changed the settings to 800X600 and it worked!

Thanks!
~lynda

---

### Post by jakornblum on 2008-04-04
WARNING:
I did this and the Windows XP boot option I had in my GRUB menu was erased....

---

