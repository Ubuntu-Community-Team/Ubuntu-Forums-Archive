---
title: "Questions with new backend"
date: 2008-05-02
forum: Mythbuntu
---

### Post by uncle hammy on 2008-05-02
I have 1 HDHomeRun with my setup.  I am building a brand new backend/frontend, and am doing a fresh install on it.

The first issue I am having is when I scan channels in the backend setup.  It keeps finding and correctly assigning channels, then suddenly it starts reassigning the next scanned frequency to the previously detected channel.  For example, I consistently scan fine to channel 20, which is assigned as 41.1/41.2 (correct) then when I hit channel 24, it updates 41.1/41.2 to channel 24, which is actually 54.1.  Sometimes it only mixes up these 2 channels, sometimes it really goes crazy reassigning the previously detected channel. I scan and rescan over and over, and once in a while it gets it right, but more often than not, this happens to me.  Is there anyway I can clean this up, or easier still, exactly what tables do I need to copy from my current (soon to be only a frontend) backend/frontend, to just copy over it's channel settings.  I tried just copying 'channel' and all the channels showed up in my channel editor, but they didn't seem complete, and they wouldn't tune.

My next issue is actually more of a question.  I hadn't really planned on moving my database from my current backend to the new one, mostly because I don't have a whole lot to cry about losing right now.  However, if I could just copy the entire database over, it would be nice.  What would be the recommended procedure to successfully migrate the entire database and recordings over to the new rig?  I am currently doing daily backups of mysql on a windows box with the mysql admin software.  Will doing this also restore my frontend settings from the old machine?

Thanks,
Scott

---

### Post by murchball on 2008-05-02
I have no idea what would cause that (I have 2 HD Homeruns and I've never seen that), but have you updated the firmware?

---

### Post by uncle hammy on 2008-05-02
I have not updated the firmware since the 0305 release.  I did see this morning that a new version has been released, I will try updating it tonight.

Actually, now that I think about it, I had this problem with 7.10, and it seemed to start after the 0305 update, which I installed and then coincidentally reinstalled mythbuntu on the same day. At that time, I just kept rescanning until it got it right.  I haven't had to do a scan since, so I kind of forgot about it.

---

### Post by uncle hammy on 2008-05-06
Updating the firmware did not solve the issue.  What I ended up having to do for now is run the scan through once, and get all my channels in,allowing 24 to overwrite 20.  Since 24 (54.1) is a crap channel anyways that I will never watch, I re-ran the scan, and after it scanned frequency 20, I cancelled it before it got to 24 to have 20 properly assigned.

Not pretty, but it worked for now.

---

