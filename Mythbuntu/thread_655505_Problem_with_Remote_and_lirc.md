---
title: "Problem with Remote and lirc"
date: 2008-01-01
forum: Mythbuntu
---

### Post by murbanci on 2008-01-01
I just tried installing a remote (ATI) on my mythbuntu machine.  I had it  working when i ran irw but never got it to do anything when i had the mythtv frontend running.  After restarting the computer irw would not run.  I would get a message like connection refused.  I tried uninstalling lirc and reinstalling but this did not work.  What do i need to do to get the remote working?  Any help would be appreciated, i am a complete n00b.  Thanks.

When i try to reconfigure the remote from the terminal this is the output that i get:

murbanci@MythTV_Box1:~$ sudo dpkg-reconfigure lirc
Stopping lirc daemon: lircmd lircd.
 * Reloading kernel event manager...
   ...done.
#####################################################
## I couldn't load the required kernel modules     ##
## You should install lirc-modules-source to build ##
## kernel support for your hardware.               ##
#####################################################
## If this message is not appropriate you may set  ##
## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##
#####################################################
Starting lirc daemon:.

---

### Post by murbanci on 2008-01-01
I tried reinstalling mythbuntu and setting up the remote durring the initial steup, however when i run irw i get connection refused.

---

