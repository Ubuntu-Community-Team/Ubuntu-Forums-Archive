---
title: "Dedicated Database Server"
date: 2010-07-30
forum: Mythbuntu
---

### Post by 7.11brown on 2010-07-30
Hi all

Here is my current setup... The main myth server has both my tuners (hauppauge 350 and HDHR) as well as the primary storage directories and database.  I also have a low power household server that is already managing local mysql databases (wordpress).

Since in my current setup, I don't want my my main backend running all the time, I was thinking of just using the low power server to hold the database and (still to fix the bugs) use wakeonlan to boot the current backend with the tuners. 

I installed mythtv to the low power server and configured it with a new myth database.  I set the main myth server to connect to the low power server in mythtv-setup, but I am uncertain as to how to complete the setup where the low power server will only manage the DB (and do mythfill) but not own any tuners.  

So in a nutshell, I want to have a dedicated DB Server that will only manage the mythtv database actions (and mythweb, which is easy enough once the DB works).  Storage will still be on the old backend with the tuners. 

Any Help is appreciated and clarification can be given if asked for


--Dan

---

### Post by nickrout on 2010-08-01
[LIST=1]
[*]this has been discussed on the main mythtv-users mailing list at length and I suggest you search them [http://www.gossamer-threads.com/lists/mythtv/](http://www.gossamer-threads.com/lists/mythtv/)
[*]My recollection is that you will need to configure the low power machine as a master backend and the ones with tuners as slave backends; however
[*]I believe at one stage there was a restriction such that your master backend had to have at least one tuner. I am not sure if this is still the case. The main list archives, or a question there, will clarify.
[/LIST]

---

### Post by newlinux on 2010-08-01
The master backend need not have any tuners. Mine doesn't (and hasn't since .20). Installing the master backend on the low power machine with the DB and mythweb should work fine.

---

### Post by nickrout on 2010-08-01
> **newlinux said:**
> The master backend need not have any tuners. Mine doesn't (and hasn't since .20). Installing the master backend on the low power machine with the DB and mythweb should work fine.

thanks for the update.

---

### Post by red321 on 2010-08-03
The only real restriction with this approach is that LiveTv is unusable. The master backend will not wake slaves to use their recorders ( by design).

---

