---
title: "How to upgrade from MythTV 0.27.0 to 0.27.4 on 14.04 for Schedules Direct"
date: 2014-10-20
forum: Mythbuntu
---

### Post by anoldguy on 2014-10-20
How do I upgrade MythTV from Fixes/0.27.0 to 0.27.04 on Ubuntu 14.04 64 bit desktop to meet the Schedules Direct changes? 

This is MythTV (not Mythbuntu, there is no Mythbuntu Control Center for me). 

I installed MythTV using Ubuntu Software Center.  

I looked at the MythTV Wiki for Ubuntu installation.  There are instructions on getting developer-builds, but I don't want bleeding-edge versions.  There are instructions for compiling MythTV, but I spent a day trying to compile and fix problems before I gave up and went to the MythTV in Ubuntu Software Center. 

I would like to use apt-get to grab the 0.27.04 release version, but I do not know how to point to it.  

Can someone tell me how to do this please?  I'd hate to poke around and break my live system (3 years and 1706 current recordings).

---

### Post by tgm4883 on 2014-10-21
> **anoldguy said:**
> How do I upgrade MythTV from Fixes/0.27.0 to 0.27.04 on Ubuntu 14.04 64 bit desktop to meet the Schedules Direct changes? 

This is MythTV (not Mythbuntu, there is no Mythbuntu Control Center for me). 

I installed MythTV using Ubuntu Software Center.  

I looked at the MythTV Wiki for Ubuntu installation.  There are instructions on getting developer-builds, but I don't want bleeding-edge versions.  There are instructions for compiling MythTV, but I spent a day trying to compile and fix problems before I gave up and went to the MythTV in Ubuntu Software Center. 

I would like to use apt-get to grab the 0.27.04 release version, but I do not know how to point to it.  

Can someone tell me how to do this please?  I'd hate to poke around and break my live system (3 years and 1706 current recordings).

Install mythbuntu-control-centre (it's in the repos) and upgrade via the repos

---

### Post by anoldguy on 2014-10-21
Wow, thank you very much tgm4883!  Works fine; no more angst. 
I did not know that Mythbuntu Control Centre worked for the plain Ubuntu MythTV. 

Here are some expanded instructions for people at my level and newer: 

- - - - -
(This is a good time to make a back-up copy of your MySQL database.  It holds your channel settings, recordings information, schedule information, and other items.  See the mythtv.org/wiki/Database_Backup_and_Restore site for details.)

Open a terminal window

sudo stop mythtv-backend
(I read on a web page that you should shut down the MythTV BackEnd process before backing up the MySQL database.  Don't know if it is required; I'm playing it safe.)

./mythconverg_backup.pl --verbose
(The . is a command to run a script, /mythconverg_backup.pl is the location of the MythTV database backup script, and--verbose is a command to show you detail information for the script)
- - - - -

Now to install Mythbuntu Control Centre:

sudo apt-get install mythbuntu-control-centre
(sudo is a command to make your terminal session the super-user (it will ask for your password), apt-get is a package handler, install is the apt-get command, and mythbuntu-control-centre is the name of the package.  centre is United Kingdom spelling and not a typo.)

exit
(command to close the terminal window)


find the Mythbuntu Control Centre app 

click on Repositories

click on Activate MythTV Updates Repository

click on Refresh available repositories

click on Apply


run the Ubuntu Software Updater and update

---

