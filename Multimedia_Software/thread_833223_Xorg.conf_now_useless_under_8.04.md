---
title: "Xorg.conf now useless under 8.04?"
date: 2008-06-18
forum: Multimedia Software
---

### Post by Mark Phelps on 2008-06-18
Have three very different machines, all were running Ubuntu 7.10 (actually, one was running Xubuntu 7.04), but anyway, got full screen resolution on all three by default.

Then, upgraded each one to 8.04, one through in-place upgrade, others through clean install.

In two cases, made a very trivial change to xorg.conf and machines were automatically set to 800x600 resolution.  In both cases, saved the initial xorg.conf file and restored it.  In both cases, still not able to get back to 1024x768.  Added modelines and display modes to each machine's xorg.conf (weren't in the originals).  Even then, can't get beyond 800x600.  Did dpkg-reconfigure xserver-xorg on both machines.  Still can't get above 800x600.  It's as if the xserver is ignoring all resolution settings in the xorg.conf now!

As a test, used liveCDs for PCLinuxOS (Mandriva derivative).  On both machines, able to load 1024x768 resolution by default.

So, it's not a generic Xserver problem; it's related specifically to Ubuntu 8.04 versions.

Is there somewhere else now that we specify screen resolutions, now that the xorg.conf file seems to be ignored?

---

### Post by horan116 on 2008-06-18
Are your video card drivers installed

---

### Post by AdamWill on 2008-06-18
Depends a lot on your driver. Check /var/log/Xorg.0.log , there'll likely be useful details in there.

---

### Post by Pjotr123 on 2008-06-18
Ubuntu 8.04 has a new system for recognition of video hardware. Most things have been lifted out of xorg.conf. You can use the command ```
gksudo displayconfig-gtk
``` for tweaking now.

However, do this first:
[http://ubuntutip.googlepages.com/nodisplay](http://ubuntutip.googlepages.com/nodisplay)

---

### Post by Mark Phelps on 2008-06-18
Gee -- thanks for all the replies!! I'm impressed -- really!

Responses:
-- video drivers installed? Don't know.  But originally, was able to get 1024x768 resolution by default on the machines without having to do anything.  Don't understand why (1) making a trivial change to the xorg.conf file should suddenly force me to 800x600 mode and, (2) restoring the original xorg.conf would NOT restore my 1024x768 mode.
-- xorg log: forgot about that.  I'll take a look at that.
-- running the configure command.  Xrandr, which used to list 1024x768 as the maximum resolution now lists only 800x600.  But I'll give this other configure command a try.

---

### Post by Mark Phelps on 2008-06-18
Followup: ....

1) video drivers: according to the xorg log file, the intel 915GM chipset video drivers are found and loaded.
2) Xorg log: looked through it. No errors. Couple of minor warnings.
3) using displayconfig: Isn't this the same as the old Screen Resolution panel?  

Anyway ... rebooted the machine and now have 1024X768 back.  Don't ask me why it didn't return during my repeated Xserver restarts; don't know.

Will try these on the other machine at home to see what happens.  Again, thanks for all the help.

---

### Post by Mark Phelps on 2008-06-19
Last update:

Tried the displayconfig command on the other laptop.  Restored the 1024x768 resolution.

Thanks for the info.

---

### Post by pietjanjaap on 2008-06-19
dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

### Post by bazzer on 2008-06-24
so what happens when you want to set your screen res on the command line? You use something like ```
xrandr --output default --mode 1280x1024
``` yeah?

---

### Post by pkslot on 2008-07-04
> **Pjotr123 said:**
> Ubuntu 8.04 has a new system for recognition of video hardware. Most things have been lifted out of xorg.conf. You can use the command ```
gksudo displayconfig-gtk
``` for tweaking now.

However, do this first:
[http://ubuntutip.googlepages.com/nodisplay](http://ubuntutip.googlepages.com/nodisplay)

This really made my day, after the 8.04.1 update. I installed the 8.04.1 again, updated, installed the nvidia drivers (which forced me into a 800x600 res) and ran "your" command, selected my preferred res.... and hey what do ya know, it works :)

Thanks man.

---

### Post by P S McDermott on 2008-07-04
You also made my day as well. Spent days trying to fix the problem. Visiting the Ubuntutip site did the trick!!

---

