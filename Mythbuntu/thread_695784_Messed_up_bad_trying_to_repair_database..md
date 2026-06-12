---
title: "Messed up bad trying to repair database."
date: 2008-02-13
forum: Mythbuntu
---

### Post by larsolav on 2008-02-13
How do you restore the weekly database backup? I think I lost all the database info. 

While recording and commercial flagging Boston Legal yesterday, I figured I would delete some old recordings. I guess my system didn’t like that, and then hung up on me. After rebooting no recordings were available with the backend still running. The backend log said that the recorded database was broken and needed to be fixed. I tried going to the control center via the Mythbuntu setup menu, but after entering my user password only got a blue wavy screen for a few seconds and then the Mythbuntu setup menu came back. I then SSH into the box and used mysqlcheck in various configurations. Eventually it removed all the lines form all the tables. (That doesn’t sound good, right?). 

Anywho, now after reboot and while starting up again it performs some kind of check disk, and then ubuntu loads up and does not enter the frontend. I have tried starting the frontend by right clicking the mouse and selecting Frontend from the drop down menu.

I’d like to keep my recordings in /var/lib and just reinstall mythbuntu in the appropriate partition (I have the /, /home, and /var/lib partitions). Can I do that and then import the automatically backed up recorded database to access my old recordings? Or should I just give the box a clean sweep install and forget about the old recordings (mostly PBS shows for the kids)?

Thanks for explaining a newbie how things are done.

---

### Post by tgm4883 on 2008-02-16
Unfortunatly you cannot reinstall in that way.  /var has to be formatted during the install (don't know if that is a bug or by design).  Have you tried running the repair database options in mythbuntu-control-centre?

The other option would be to back up the db and the shows to another HD, then reinstall and transfer them back

---

### Post by larsolav on 2008-02-16
I did try to get into the control center, but that was one of my problems: I could not load it...
So I bit the dust yesterday and copied everything to an external HD. Luckily I had just in late December upgraded my system so I had then dumped the recorded data into a file, so I only lost database information from January and February! 
Everything works fine. At least for now.
Thanks!

---

