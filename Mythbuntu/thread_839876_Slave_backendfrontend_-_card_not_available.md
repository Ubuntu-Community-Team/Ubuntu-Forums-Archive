---
title: "Slave backend/frontend - card not available"
date: 2008-06-24
forum: Mythbuntu
---

### Post by Panhead Bill on 2008-06-24
I'm trying to get my slave Be/Fe running. This will be the visible unit, with the master Fe/Be set up in the basement.

Problem:  If I shutdown the slave, the master lists the HPG-350 as "Not available".  When I start the slave up, the card status is still "Not Available".  I have to go into, and out of mythsetup on the slave to get the card listed as "available".

I'm not changing any settings in setup, just checking that all of the card and input settings are as they should be.  When I quit mythsetup, the card status on the master changes to "Not recording" like the two cards on the master.

Any ideas?

---

### Post by volkswagner on 2008-06-24
You should post your backend.log files, for both machines.  Check the stick if you are not sure how to get your log files. 

I had a similar problem.  The fix for me was to set the machines to static IP's, no roaming.

---

### Post by novellahub on 2008-06-25
Restart your mythtv backend on the slave box and your tuner should reappear.  It is a small quirk that happens with machines without static IP's.

```

sudo /etc/init.d/mythtv-backend restart

```

---

### Post by Panhead Bill on 2008-06-25
Both boxes, the master and slave have been set up as static addresses from the start.  I will try the restart anyway, to see if it changes anything.

A side issue, when I go into Mythsetup on the slave, it creates another "Wired Internet connection" icon in the left side of the top menubar.  I currently have 5 of the icons.

---

### Post by volkswagner on 2008-06-25
You may try to uncheck the network manager in auto start programs.

---

