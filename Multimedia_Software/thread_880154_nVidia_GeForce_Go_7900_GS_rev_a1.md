---
title: "nVidia GeForce Go 7900 GS rev a1"
date: 2008-08-04
forum: Multimedia Software
---

### Post by trickyidiot on 2008-08-04
I have a Dell XPS M1710 Laptop with an nVidia GeForce Go 7900 GS (rev a1) Video Card.

When trying to run 'compiz' from the terminal, I recieve the following output:

Checking for Xgl: not present.
No whitelisted Driver found
aborting and using fallback: /usr/bin/metacity

I tried going into System > Administration > Hardware Drivers, unchecking the nvidia_new driver, restarting and then rechecking the nvidia_new driver and restarting to no avail.

In that window, although the nvidia_new is checked, to the right of it is a red dot that says 'Not in use'. I'm not sure why.

I openly admit that I am a novice user. I have gone through this (and several other) forums with no luck.

What else can I do at this point to get compiz fusion working?

Thanks in advance.

-=Tricky=-

---

### Post by overdrank on 2008-08-04
Hi and welcome. you may try what PmDematagoda suggested here
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
the disable the drivers reboot and the enable them again.
Moved to general help. :)

---

### Post by trickyidiot on 2008-08-05
I made the change you suggested to /etc/default/linux-restricted-modules-common and restarted my machine.

There is no change other than the driver no longer showing up in System > Administration > Hardware Drivers.

I receive the same errors when trying to run 'compiz' from shell.

---

### Post by trickyidiot on 2008-08-05
Also, I apologize for initially posting in the wrong forum

---

