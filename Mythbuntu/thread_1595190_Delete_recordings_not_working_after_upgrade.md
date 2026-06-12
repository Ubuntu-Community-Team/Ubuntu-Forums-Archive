---
title: "Delete recordings not working after upgrade"
date: 2010-10-13
forum: Mythbuntu
---

### Post by kurt2000 on 2010-10-13
Hi

Hi, i recently upgraded my ubuntu 9.10 to 10.10.

A lot of problems solved, but 1 remains. I cannot delete recordings through mythweb or frontend, really strange.

And now the recordings will fil up my drive, Mhh.

Anyone having good tips on how to debug this problem ?

With kind regards
Kurt2000

---

### Post by PaulReaver on 2010-10-13
in mythbackend in general options on the miscellaneous settings page
have you ticked the 'Follow symbolic links when deleting files' box?

if not it'll just delete the entry in the database and leave the file, then later when mythbackend scans for files it'll magically reappear... :)


I hope this helps.... you never know it might be something else..

---

### Post by kurt2000 on 2010-10-13
Hi

Thanks for the reply. I don't use symbolic links, so enabling that setting didn't change anything.

When i try to delete from mythweb, nothing happens. There use to be a little green popup in the lower left corner, but that dosen't show anymore.

Wkr.

---

### Post by novellahub on 2010-10-13
Did your hostname change on the machine?  That could affect deletion of the files.

Check your log files when attempting to delete them to get more clues:

```

tail -200 /var/log/mythtv/mythbackend.log
tail -200 /var/log/mythtv/mythfrontend.log

```

---

### Post by rhpot1991 on 2010-10-13
Check that slow deletes isn't enabled in mythtv-setup.  This can sometimes delay deletes and make it seem like things are not deleted.

---

### Post by kurt2000 on 2010-10-14
Hi,

I was wrong about the frontend, i can delete recordings through the frontend.

Its only mythweb that dosn't work.

Nothing shows up in the backend log indicating that there is a call to the backend, so i guess it's mythweb that's broken or the comunication with the backend.

Any sugestions on how to debug that ?

Wkr.

---

### Post by kurt2000 on 2010-10-17
Hi

Ok, don't know what happened, now i can delete recordings again...

Thanks for your effort in solving my problems.

Wkr.
Svend

---

### Post by rhpot1991 on 2010-10-18
Smells like slow deletes is on, did you check it?

---

### Post by kurt2000 on 2010-10-18
yeah, i did check it. No i think there was something wrong with the mythweb plugin, now there is a popup, wasn't any before.

Wkr.

---

