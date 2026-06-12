---
title: "Update 9.04-&gt;9.10 mythwelcome/mythfrontend issues preventing idle shutdown"
date: 2009-11-15
forum: Mythbuntu
---

### Post by Morgennebel on 2009-11-15
Hi there,


I recently updated my combined Backend/Frontend Mythbuntu 9.04 installation to 9.10. Running at 9.04 everything worked like a charm (ACPI wakeup, mythwelcome loading mythfrontend via remote control or idle shutdown after recording).

Since I upgraded I experience issues with mythwelcome which prevents the system to shutdown after a successfull finished recording (and yes, in mythtv-setup I disabled "Wait for client frontend" :-)).

I am using auto-login to user "os". In ~os/.config/autostart/MythTV.desktop the systems loads "Exec=/usr/bin/mythwelcome" - as my old configuration "Exec=/usr/bin/mythfrontend --service" does not work anylonger, it will jump to mythfrontend instead of mythwelcome.

When the system starts I do see the mythfrontend screen which is then overwritten by mythwelcome. After a recording the running mythfrontend reports to the backend to be running and the instance prevents an idle shutdown - mythwelcome just reports "mythtv is idle".

Also I do see multiple (up to 14) mythfrontend zombie (<defunct>) processes. 

I have tested to delete the ~/.config/autostart/MythTV.desktop file. Still mythfrontend will be loaded - no clue where, how and why :-)

I found in pstree a /usr/share/mythtv/session.sh session which has been initiated from dbus. 

I would like to get back to my mythwelcome screen which is able to shutdown the system after a recording.

Any hints are welcome,

Thanks, -MN

---

### Post by leafpaul on 2009-11-16
I am getting the same behaviour although in my case "exec: mythfrontend --service" still works ie still opens mythwelcome.

On startup I get mythfrontend, a terminal window and mythwelcome all opening.  With mythfrontend and the terminal window opening before the xfce autostart process kicks in (which loads mythwelcome).

Something is starting mythfrontend itself directly (ie not via mythwelcome) before the ~/.config/autostart/mythtv-desktop script runs.

---

### Post by jerryscuba on 2009-11-16
Have you checked if the frontend is selected in Application Autostart?
If in Session Startup - General - Logout Settings the Option Automatically save session on logout is selected, the frontend would start if it was running at shutdown.
In addition I would check that Grub is starting the newest Kernel. I had this and many other issues because I was still running an older Kernel after the 9.10 upgrade.

Good luck

---

### Post by leafpaul on 2009-11-16
No running 2.6.31-15-generic and only mythwelcome is running at shutdown.

---

### Post by leafpaul on 2009-11-17
I deleted the contents of ~/.cache/sessions/ which cleared the problem.

---

### Post by screwbunt2 on 2009-11-28
Thanks, **clearing the cache folder** helped fix my problem also.

I did the same update 9.04 to 9.10, and the problem I was having was after mythwelcome started. I was also getting mythbuntu-control-centre starting up on top of mythwelcome everytime I booted. I don't know how I ended up here, but it worked!

---

### Post by movieman on 2009-11-29
I have a bunch of defunct mythfrontends too, and clearing the cache directory made no difference. There's no log message explaining why, and it appears that the defunct processes started after the process that's actually running.

This is definitely new with 9.10, it didn't happen with 9.04. It could be due to the changes that broke the automatic login?

---

### Post by movieman on 2009-11-29
Looks like this may be the cause of the defunct processes:

[http://svn.mythtv.org/trac/ticket/6137](http://svn.mythtv.org/trac/ticket/6137)

I created /sbin/udevinfo containing:

```
#!/bin/bash
/sbin/udevadm info $1
```

And after rebooting I don't have any defunct processes anymore.

---

