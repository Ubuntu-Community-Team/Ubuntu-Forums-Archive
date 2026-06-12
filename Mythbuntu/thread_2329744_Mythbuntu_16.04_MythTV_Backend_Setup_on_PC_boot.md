---
title: "Mythbuntu 16.04 MythTV Backend Setup on PC boot"
date: 2016-07-04
forum: Mythbuntu
---

### Post by rick-immel on 2016-07-04
Just completed a fresh install of Mythbuntu 16.04.  Every time I reboot the Mythbuntu machine it automatically starts MythTV Backend Setup.  I must then manually exit MythTV Backend Setup, enter the password twice to confirm MythTV Backend shutdown and then startup, and finally respond to the dialog about running mythfilldatabase.  Is there somewhere that I can disable this autostart of MythTV Backend Setup on a system reboot?

---

### Post by QDR06VV9 on 2016-07-04
See if this still works
"sudo stop mythtv-backend" and "sudo start mythtv-backend"

---

### Post by wayne36 on 2016-07-05
I too have a fresh install of Mythbuntu 16.04 and Myth .28 (both updated up to date) and have had this and other questions.  I am a longtime myth user but first time user of Mythbuntu so ...still lots of questions  My observations so far.

If you are ending up in mythtv-setup on every boot, but then can run mythbackend without ending up in the setup, you may not have configured the database and setup correctly.  Check all your my.cnfs and config.xml files.  If you check them (locate config.xml) you will find one with  localhostname  with "local-host-identifier goes here" (sorry can't remember which one specifically) I think that one was the fix for me.  

Have you changed the  mythbackend startup and shutdown commands in the backend setup?  the default in setup are:    mythbackend and killall mythbackend 

It appears there are two ways of initiating the backend - either from the menus or from a terminal.  Killing the backend takes one of two ways

If you do it from the menu- it needs sudo,  if you do it from a normal user terminal it doesn't.

It does take a bit of time to disappear.

---

### Post by rick-immel on 2016-07-05
This problem turned out to be easier to solve than I first expected.  The first time Mythbuntu boots up after installation it goes to the XFCE desktop instead of the MythTV Frontend.  On the desktop are three launchers.  One is labeled "Initial Setup".  It is specified in the XFCE "Session and Startup"  dialog as an autostart application.  I simply had to go to the "Application Autostart" tab of the "Session and Startup" dialog and uncheck the "Initial Setup" launcher to suppress the auto start of MythTV Backend Setup at boot time.

---

### Post by gga96 on 2016-10-04
I have the same boot auto setup and on exit the need to sign twice etc, but now I finish at a blank screen, the only thing I can do is use "Ctrl Alt 1" to open a terminal.

The terminal prompts me to log in, I then have terminal access to my system, but no GUI only the command line.

I would like to follow your fix: > I simply had to go to the "Application Autostart" tab of the "Session  and Startup" dialog and uncheck the "Initial Setup" launcher to suppress  the auto start of MythTV Backend Setup at boot time. but I have to do it from the terminal.

Have you any thoughts on how to do that from the terminal?

---

