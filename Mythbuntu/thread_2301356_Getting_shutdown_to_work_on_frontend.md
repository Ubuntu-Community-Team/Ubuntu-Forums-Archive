---
title: "Getting shutdown to work on frontend"
date: 2015-11-01
forum: Mythbuntu
---

### Post by jonathan.k3 on 2015-11-01
I apologize if this has been asked before but googling has only given me some half-answers. How do I get my frontend to actually exit & shutdown when I choose that option? Right now I'm exiting mythtv and then log out -> shutdown in the ubuntu desktop. BTW, I have a separate backend.

I'm seeing something about editing a sudoers file:
[http://www.gossamer-threads.com/lists/mythtv/users/580597](http://www.gossamer-threads.com/lists/mythtv/users/580597)

As well as some info on running a script in the settings but I'm not sure what the exact steps are. Are both necessary or are they not needed for 14.04.3?

---

### Post by blm-ubunet on 2015-11-03
Lots of different ways to configure shutdown..

Can exit FE & logout.
Can just exit FE only.
Can exit FE into mythwelcome.
I believe can use exit/sleep timer in FE.

Allowing BE to shutdown potentially enables it to set the wakeup alarm in BIOS for any pending recordings.
[https://www.mythtv.org/wiki/ACPI_Wakeup](https://www.mythtv.org/wiki/ACPI_Wakeup)
Don't have to use wakeup-alarm to utilise shutdown.

The sudoers file (must only edit with visudo) changes (in my link & yours) allow MBE user "mythtv" permission to run privileged programs.

You have to configure the BE to run the supplied scripts on key events (like idle). These are listed in an obvious manner by mythtv-setup.
These scripts can check if users are logged in &/or set wake-alarm etc..

---

### Post by jonathan.k3 on 2015-11-08
Thanks for the info, blm-ubunet.

I was looking for a way to get the last option to work "Yes, Exit and Shutdown" on the menu that appears when you press ESC on the frontend. Before, when I pressed it nothing happened. Based on the info in here: [http://www.gossamer-threads.com/lists/mythtv/users/580597](http://www.gossamer-threads.com/lists/mythtv/users/580597). I did:

In terminal: **sudo visudo -f /etc/sudoers.d/mythtv**
Then in the file: **<username> ALL = NOPASSWD: /sbin/poweroff, /sbin/reboot, **
**/sbin/shutdown, /sbin/halt**
where <username> is the name of the user that runs the frontend (i.e. the 
one that you can't call mythtv!!) 

Can use **whoami** in terminal if you don't know what your username is.

Now it works and the frontend devices shutdown when I choose "Yes, Exit and Shutdown".

---

