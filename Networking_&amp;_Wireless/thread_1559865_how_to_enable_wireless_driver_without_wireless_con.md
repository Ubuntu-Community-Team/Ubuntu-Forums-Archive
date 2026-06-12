---
title: "how to enable wireless driver without wireless connection?"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by superarthur on 2010-08-24
my laptop has a proprietary Broadcom STA wireless
while in live CD, I can go system>administration>hardware drivers, and activate the driver
however, when I have ubuntu installed into the hard drive, and go to system>administration>hardware drivers, ubuntu attempts to connect to the internet to look for the driver and fails
I can't find the option to choose the driver in the computer. I even inserted the live CD into the disc drive, and still no luck.
How to install the wireless driver without wireless connection?
Is it possible to install the driver manually?

---

### Post by bkratz on 2010-08-24
> **superarthur said:**
> my laptop has a proprietary Broadcom STA wireless
while in live CD, I can go system>administration>hardware drivers, and activate the driver
however, when I have ubuntu installed into the hard drive, and go to system>administration>hardware drivers, ubuntu attempts to connect to the internet to look for the driver and fails
I can't find the option to choose the driver in the computer. I even inserted the live CD into the disc drive, and still no luck.
How to install the wireless driver without wireless connection?
Is it possible to install the driver manually?

As you have found out the STA driver is actually on the CD. Try going to System>>Administration>>Software Sources and put a check in the box labeled "Installable from CD Rom" and try again. I can't remember the exact path to those drivers, but will find it and repost if you need it.

---

### Post by bkratz on 2010-08-24
Here are the step from another posting
"
From LiveCD (solution provided by jomtois here - edited for clarity):
Open Sytem -> Admin -> Synaptic Package Mgr
Ensure  LiveCD is in the drive
In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
Check "Installable from CD-ROM/DVD" and close
Reload (disregard connectivity errors)
Search for "bcmwl-kernel-source"
Right-click and mark for installation
Apply changes and reboot


"

---

### Post by superarthur on 2010-08-24
Thanks a lot. I am going to try it.
(The problem is that I obvious can't go back to this post while I am in Ubuntu without wireless, and I may not remember all the steps :P)

---

### Post by superarthur on 2010-08-24
> **bkratz said:**
> Here are the step from another posting
"
From LiveCD (solution provided by jomtois here - edited for clarity):
Open Sytem -> Admin -> Synaptic Package Mgr
Ensure  LiveCD is in the drive
In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
Check "Installable from CD-ROM/DVD" and close
Reload (disregard connectivity errors)
Search for "bcmwl-kernel-source"
Right-click and mark for installation
Apply changes and reboot


"

I did everything you say.
I went to system>administration>hardware drivers and clicked "activate" for the Broadcom STA wireless driver
but it came up with this error message:

SystemError: installArchives() failed

---

### Post by bkratz on 2010-08-24
Here is a very similar thread I found with googlubuntu, 

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

[http://ubuntuforums.org/showthread.php?t=1498606](http://ubuntuforums.org/showthread.php?t=1498606)

there were actually quite a few when I used that tool (very handy) and looked for that error.  There were a lot of postings but most concerned video.  There is a complete description there, but I believe they eventually solved it by using an ethernet connection. Hopefully something there will help. I will continue to look though.

---

### Post by bkratz on 2010-08-24
This link was just posted in another thread, probably worth looking at

[http://ubuntuforums.org/showthread.php?t=1559025](http://ubuntuforums.org/showthread.php?t=1559025)



Here another, see post 6 first.

[http://ubuntuforums.org/showthread.php?t=1559749](http://ubuntuforums.org/showthread.php?t=1559749)

---

### Post by superarthur on 2010-08-24
> **bkratz said:**
> This link was just posted in another thread, probably worth looking at

[http://ubuntuforums.org/showthread.php?t=1559025](http://ubuntuforums.org/showthread.php?t=1559025)



Here another, see post 6 first.

[http://ubuntuforums.org/showthread.php?t=1559749](http://ubuntuforums.org/showthread.php?t=1559749)

I used the commands from post 6, but still nothing happened.

---

### Post by superarthur on 2010-08-24
can somebody help please?
I think it's an important bug. If it runs smoothly on a live CD, it should do the same when installed onto the hard disk.

---

### Post by superarthur on 2010-08-25
I've even tried downloading the .deb package from here:
[http://packages.ubuntu.com/da/lucid/bcmwl-kernel-source](http://packages.ubuntu.com/da/lucid/bcmwl-kernel-source)
and still no luck...

---

### Post by superarthur on 2010-08-26
I finally solved it!!!
(sorry for the quadruple posting, but I think a lot of people encounter the same problem with wireless drivers, so I am going to post the solution here)

Activate the wireless driver from live CD first, and then install ubuntu onto your hard drive
The activated driver would be carried over to the proper installation.
I hope it helps others like me who has problems with broadcom drivers.

---

