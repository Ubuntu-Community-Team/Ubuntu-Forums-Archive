---
title: "[SOLVED] protocol mismatch"
date: 2008-02-09
forum: Mythbuntu
---

### Post by Tteddo on 2008-02-09
I have Mythtv running a frontend and a backend in my living room, and a laptop in my office with only the frontend. Since I updated both the one in the living room the other day, and the laptop, the laptop fires up the frontend, but when I try to do anything I get an error:
"The server uses network protocal version 39, but the client only understands version 31"

The laptop is regular Ubuntu and the main machine is Mythbuntu and looks like it is running a trunk version different from the laptop?

Is there a way to get the laptop to automagically keep synch with the version that the backend is running?

---

### Post by superm1 on 2008-02-09
You've got a trunk build installed.  This can be caused by 1 of 3 things:

1) You are on Hardy
2) You are on gutsy using weekly trunk builds
3) You got caught by the mistake this week with trunk builds getting on the wrong repo.

If the answer is (3), there was a mistake that after a trunk build failed on the mythbuntu-trunk repo, it got pushed to the mythbuntu repo.   If this is on your frontend only (no backend on this box), the good news is that you can just roll back to the correct version.  If its on the backend, you will also need to restore your database.  It got backed up automatically before the upgrade into /var/.

Alternatively, you can activate the trunk weekly builds on all your boxes.  It's actually fairly stable (hence why its in hardy now).  Upstream is preparing to release 0.21 in the very near future.

---

### Post by Tteddo on 2008-02-09
It must be 3)...
How do I activate the trunk weekly builds on all my boxes, or roll it back?
Which would you do?

---

### Post by superm1 on 2008-02-09
> **Tteddo said:**
> It must be 3)...
How do I activate the trunk weekly builds on all my boxes, or roll it back?
Which would you do?
Well i personally switched all mine to trunk builds already.  Like I said they are fairly stable now. 

If you want to roll back, then you will need to use synaptic and hit ctrl-e on any packages that need backrolling.

---

### Post by Tteddo on 2008-02-09
Ok, You are the expert, I'll go with the trunk builds, is it easy to do that?  
I'll take the trunk builds for $300 Alex!

---

### Post by superm1 on 2008-02-10
> **Tteddo said:**
> Ok, You are the expert, I'll go with the trunk builds, is it easy to do that?  
I'll take the trunk builds for $300 Alex!
If you already have weekly builds on, just modify your source in sources.list or mythbuntu-gutsy.list (wherever you put it) to add a -trunk like described here:
[http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds)

---

### Post by Tteddo on 2008-02-10
In thinking about it over night, before I do anything I want to be clear. 
Since the accidental switch to trunk did actually break some things like viewing videos and a couple of other things like the internal web site (disregarding the other frontend problem), I think I need to roll things back.
If I do the roll back on mythfrontend and mythbackend in Synaptic will all the other things associated with MythTV roll back also to maintain dependencies?
If not, can I just do a search for "mythtv" and roll back everything it finds?

For the database part I see the backup in there from last Tuesday. If I restore that it will orphan recordings since then, right? I could just copy them out of the recordings folder first?

---

### Post by Tteddo on 2008-02-12
Ok, I went ahead and rolled back everything myth related I could find, and all the functions came back, and they work except watching TV and recording.
My capture cards disappeared in MythTV Backend Setup. When  try to add them back in (it's a Hauppage 500) it goes through, then I hit finish and it goes back to the 1st Capture card screen with no entries under it instead of /dev/video0 and /dev/video1 like there used to be. They were still there even after the bad trunk update last week.
Anyone have any ideas on how to fix this? Is there something I can roll back that is not found by searching for mythtv?

---

### Post by ian dobson on 2008-02-13
Hi,

Try deleting all the cards, exiting then going in again and add your cards again.

I had to do this when going from a PVR-150 to a 500.

Regards
Ian Dobson

---

### Post by Tteddo on 2008-02-13
That's the problem, there are no cards in there anymore and when I try to add them back in it just goes back to the Capture Cards screen with nothing in there.

---

### Post by ian dobson on 2008-02-14
Hi,

Even if the system says there aren't any cards, select delete all then save/exit and try adding your tuners again.

I know it sounds abit strange, but please try it out.

Regards
Ian Dobson

---

### Post by Tteddo on 2008-02-14
Ok, I'll try it as soon as my power comes back on! :(

---

### Post by Tteddo on 2008-02-14
Ok, I tried that, and as soon as I confirm that I want to delete them it either kicks me out of the mythbackendsetup or says that it can't do that.
Either way it is still the same when I try to add.
When I try to add it does see my card in the probed info, incidentally.

---

### Post by ian dobson on 2008-02-15
Hi,

OK, it sounds as if you have a database miss match. Which backend are you running now (trunk,svn etc)?

Maybe the best idea is to uninstall the mysql mythtv package and then reinstall it. This should clear out your database. You will loose all your settings but atleast youll have a running system.

Regards
Ian Dobson

---

### Post by Tteddo on 2008-02-15
How does the database affect MythTV seeing the capture card? Just asking.

You are probably right though, I didn't restore the backup from before the bad upgrade I still have it in /var/backups. Everything else was working, so since I couldn't see how that could affect the problem I was having I didn't restore it.
Do you know of instructions on restoring the backup?

---

### Post by Tteddo on 2008-02-21
Ok, I can take a hint! I'll rtfm on the restore:)

But I would really like to know why the database affects the hardware? What's the purpose of that, and why? In thinking about it, why can't I restore to a different  database and copy the appropriate table over?

---

### Post by Tteddo on 2008-02-25
I finally got back to this.
I found some instructions on the database restoration here:
[http://www.uluga.ubuntuforums.org/showthread.php?t=384511]("http://www.uluga.ubuntuforums.org/showthread.php?t=384511")
and that worked great. After a reboot to get everything back on the same page, everything "just worked" again, including all my recording settings.

To answer my own questions, I poked around in the mythconverg database and there are 2 tables, "capturecard" "and "cardinput" that are used to track the capture cards. They must have a different setup in the newer database I accidentally upgraded to.

All better now, thanks ian dobson!

---

