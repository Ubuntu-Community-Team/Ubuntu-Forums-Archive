---
title: "Power management in Mythbuntu"
date: 2007-12-28
forum: Mythbuntu
---

### Post by Jeff13 on 2007-12-28
I am building a Mythbuntu HTPC as my first Linux project and so far so good.  I can watch and record TV, but I am having trouble getting the device to power down between TV recordings and I was wondering if there is a way to manage the power management settings in Mythbuntu?  I downloaded the Gnome ACPI setting that is normally in System>Preferences (Ubuntu), but there is no Preferences menu in Mythbuntu and I cannot find it anywhere else.  I have set the system to shutdown after 10 minutes of inactivity in MythTV, but I haven't filled in any wake up commands in the MythTV setup screen (because I have no idea what a wakeup command is).  When I try to manually hibernate the system, it refuses.  It says something like "Stopping kernel threads, timed out after 20 secs, one task refusing.
lirc_dev"

Any suggestions greatly appreciated.

---

### Post by JeepFreak on 2007-12-28
Great question... this is on my To-Do list also.
Billy

---

### Post by Naoi on 2008-01-02
Here's the answer to lirc_dev refusing to stop from this thread [http://ubuntuforums.org/showthread.php?t=408511]("http://ubuntuforums.org/showthread.php?t=408511")  on the general help board.  You basically have to unload two processes (lirc_i2c and lirc_dev)  in the proper order when you try to suspend.


> **chosebin said:**
> hi,

After a week, I managed to get suspend-to-ram to work on Ubuntu 7.10! You cannot kill lirc_dev, because it is a kernel module. However, you can unload it with the rmmod command:

- sudo su
- rmmod lirc_dev

If you get an error similar to:

 ERROR: Module lirc_dev is in use by lirc_i2c

It means lirc_i2c (or another module specific to your hardware) depends on lirc_dev, and you need to unload it first. To do this:

- sudo su
- rmmod lirc_i2c /* whatever dependency you get in the error message */
- rmmod lirc_dev

By running those commands, you should be able to suspend your machine, if you don't have a driver problem like I had for a week :) After a resume, you can reload those modules with:

- sudo su
- modprobe lirc_dev
- modprobe lirc_i2c /* whatever dependency you get in the error message */

If suspend-to-ram works for you after unloading lirc_dev, you will probably want to unload automatically those modules when you suspend your machine and load them automatically when you resume your machine. To do this, in the file /etc/default/acpi-support, change line:

- MODULES=""

by

- MODULES="lirc_i2c lirc_dev"

Be careful to insert lirc_i2c (or anything else) before lirc_dev.
--------------------------------------------------------------------------------------
Nices resources to know on Ubuntu 7.10 and related to ACPI S3 (Suspend-to-Ram)

/etc/acpi/ -> scripts for ACPI
/etc/default/acpi-support -> configuration file for scripts in /etc/acpi
/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux -> script executed by gnome to suspend to ram
/proc/acpi/alarm -> modify to set a wakeup time (if supported by mobo)

I can't help much past that issue.  I was at this point a few weeks ago and once suspend/resume worked I had issues where MythTV didn't run properly after resuming from suspend.  Sometimes it ran OK, other times it was suposedly running but nothing displayed.  I've been too busy to get back to it since.

Good luck :)  If you get farther than I did please post how you did it. :)

---

### Post by volkswagner on 2008-01-02
Some other threads you may or not have read.

[http://ubuntuforums.org/showthread.php?t=637610]("http://ubuntuforums.org/showthread.php?t=637610")

[http://ubuntuforums.org/showthread.php?t=566642&highlight=acpi]("http://ubuntuforums.org/showthread.php?t=566642&highlight=acpi")

Myth Welcome is of high importance for proper wake I believe.

---

### Post by Jeff13 on 2008-01-05
Thanks Naoi.  Your forwarded instructions got suspend/hibernate to work.  When I would resume, I just got a blank screen, but I remarked out (#) the POST_VIDEO=true line in the acpi-support file and it resumed just fine.  I still haven't incorporated all the suggestions re. MythTV and shut-down/wake commands, nor have I looked at MythWelcome yet, but I'll post again if I resolve any problems like you described.

Thanks again Naoi and volkswagner!:)

---

