---
title: "How to set up backend?"
date: 2009-09-05
forum: Mythbuntu
---

### Post by torbengb on 2009-09-05
Hello! I'm a total Linux newbie but want to get away from Windows on my media center pc. I've installed Ubuntu 904 (which looks great!) and also installed Mythbuntu on top of that using [http://mythbuntu.org/download/getmythbuntu.php](http://mythbuntu.org/download/getmythbuntu.php)

I've clicked through the Mythbuntu Control Centre but when I click on "launch mythtv setup" I'm at a loss for what to do. I answer OK to close mythbackend and then a terminal window flashes by in which I notice the line "database not open". The setup "wizard" that appears (no mouse cursor?) repeats that no database was found.

Obviouly I must've missed something but I can't see what to do in order to establish the required database. I also didn't find a similar question here. Your responses will be very much appreciated!

---

### Post by itlarson on 2009-09-05
Just a guess, but did you look at the "system roles" section?  I'm pretty sure the database should be set up for you, but it wouldn't be  if you had opted for a front-end only.

---

### Post by torbengb on 2009-09-05
System Roles: 
Backend role: primary backend
Frontend role: Frontend
Desktop role: Ubuntu Desktop
Diskless server: (no checkboxes selected)

It seems to be what you'd expect. Also, during setup there was a message about having to start the database manually which I wisely wrote down. If I do alt-f2 and enter "sudo /etc/init.d/mythtv-backend start" as stated, nothing appears to happen (I'd expected at least a notification or an error message), and if I run the MCC afterwards it still says database not found.

Is there a way to check if the database server itself is running, and whether the database exists at all? Would it make sense to just install Mythbuntu again (overwriting the existing install, or removing and then install from scratch)?
If need be, I wouldn't mind completely erasing the Linux installation and start over, just in case that would solve anything.

---

### Post by williammanda on 2009-09-06
I installed ubuntu 9.04 and used synaptic package manger to install mythbuntu. Try removing mythbuntu (use mark for complete removal) using synaptic and re-install mythbuntu using synaptic package manager. If you still have problems start from scratch with a fresh install of ubuntu.
Thanks

---

### Post by torbengb on 2009-09-07
Thank you for the suggestions. I'm going to remove Ubuntu and then start over, just to be sure. Then I'll post here again.

First I'll install Ubuntu and then, using Synaptics as you suggest, Mythbuntu - instead of the "getmythbuntu" URL in my first post.

---

### Post by torbengb on 2009-09-08
There must have been some bad setup in the old installation because I have now completely reinstalled Ubuntu on the pc and then installed Mythbuntu on top. Now setup completes and I even get the nice big graphical onscreen menu. 

But no tuners were detected, so it wan only a small victory so far. My next question is then, obviously: 

**How do I set up my tuners?**

I have 2 different tuners, 1 Medion/Creatix and one WinFast, both are internal PCI cards and getting a cable signal. 
I'm in Austria and my cable provider is "Kabelsignal". Here's the listing: [http://www.kabsi.at/download/programme/K062.pdf](http://www.kabsi.at/download/programme/K062.pdf)

I need help about going through the (very cryptic) tuner setup and also the setup for EPG data. I know my cable company provides an EPG signal but I don't know anything about it.... In Windows it was just there...

---

### Post by tgm4883 on 2009-09-09
> **torbengb said:**
> There must have been some bad setup in the old installation because I have now completely reinstalled Ubuntu on the pc and then installed Mythbuntu on top. Now setup completes and I even get the nice big graphical onscreen menu. 

But no tuners were detected, so it wan only a small victory so far. My next question is then, obviously: 

**How do I set up my tuners?**

I have 2 different tuners, 1 Medion/Creatix and one WinFast, both are internal PCI cards and getting a cable signal. 
I'm in Austria and my cable provider is "Kabelsignal". Here's the listing: [http://www.kabsi.at/download/programme/K062.pdf](http://www.kabsi.at/download/programme/K062.pdf)


I need help about going through the (very cryptic) tuner setup and also the setup for EPG data. I know my cable company provides an EPG signal but I don't know anything about it.... In Windows it was just there...

You need to run mythtv-setup

Take a look at [http://www.mythbuntu.org/installation_manual](http://www.mythbuntu.org/installation_manual)

Grab the 8.10 manual, not a lot has changed.

---

### Post by torbengb on 2009-09-11
Thank you very much for the tip! 

Wow, a 130+ page manual... it's very detailed, but I'm stunned that it's even necessary. I am going to follow the instructions and see how it works out. I must admit that the ease of Windows is beckoning to me.

---

