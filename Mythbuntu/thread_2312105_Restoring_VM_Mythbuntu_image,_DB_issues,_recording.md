---
title: "Restoring VM Mythbuntu image, DB issues, recordings won't delete"
date: 2016-02-01
forum: Mythbuntu
---

### Post by mike_d2 on 2016-02-01
I run mythbuntu 14.04.2 in a KVM environment, and store all of my recordings on a network share. Recently the drive holding the recordings died. I added a new drive, formatted it all properly and mounted it, but when I restore my VM image, the recordings it's looking for are no longer there. How do I tell mythbuntu to forget about all of the old recordings are start fresh with a blank recordings directory? Every time I try to delete it, one old recording keeps popping up in mythbuntu's "Recorded Programs" Thanks very much in advance

---

### Post by khPWXxF on 2016-02-02
There is a utility to reconcile database and recording files called find_orphans.py
You will probably find it on your system if you do:
   ```
locate find_orphans.py
```
When you delete recordings with it note that they take a while to vanish and you may initially think that it has not worked.

hth
Phil

---

### Post by mike_d2 on 2016-02-02
I've tried this although it doesn't seem to fix my issue. When looking at the SQL database I see latin1 charsets, so I know something is wrong.

---

### Post by khPWXxF on 2016-02-02
have you tried optimize_mythdb.pl to mend your database?
Phil

---

### Post by mike_d2 on 2016-02-02
I have tried to walk through both that, and restoring and repairing the DB to no avail. I am just going to start with a fresh image. This is all started as the result of a userscript intended to flag commercials, cut them, transcode to H264, AAC (from HDHR) and give it an Title.S##E## name for upload purposes. The script does some type of lookup for the db and password and something wasn't right, borked the whole thing.  The problem I had with mythbuntu 14.04.2 was no ffmpeg proper, so I had to find and compile my own version with libx264 and it was a pain the ****. Oh well. But thanks very much for your help, I think once the myth SQL DB is broken, it's time for a fresh install or restore image. Thank you very much for your time.

---

### Post by khPWXxF on 2016-02-02
Ok, sorry to hear that.  Hope you have a good backup!
One thing did occur:

> Every time I try to delete it, one old recording keeps popping up in mythbuntu's "Recorded Programs"
Do you mean ONE re-appears? Same one?    If so, then could you try creating a dummy recording file and delete in  normal fashion?

Phil

---

