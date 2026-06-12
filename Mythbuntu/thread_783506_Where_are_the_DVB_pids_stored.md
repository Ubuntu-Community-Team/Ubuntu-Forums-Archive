---
title: "Where are the DVB pids stored???"
date: 2008-05-05
forum: Mythbuntu
---

### Post by Das Hammer on 2008-05-05
Looking for VPID, APID, PCRPID, etc. for DVB Channels.
I looked in the mythconverg database, but couldn't find table with this data.  Some googling suggested that there was a table in mythconverg called dvb_channel, but I did not see one.  Perhaps this is in an older version of the database.

So, where is this information stored?  I have DVB channels in which were scanned in and I can watch them, so they have to be stored somewhere.  :confused:

---

### Post by laga on 2008-05-06
Try the 'dtv_multiplex' table.

---

### Post by Das Hammer on 2008-05-06
Looked there, but only the frequency, symbolrate, things associated with the "transport streams" are listed there.  The channel record calls the TSID from the dtv_multiplex table.

---

### Post by laga on 2008-05-07
Ah, right. I think those are now detected automatically.

---

### Post by Das Hammer on 2008-05-07
I'm certain you know more about this than I do, but if it is doing this automatically, how can the program reliably choose the correct video and audio pids out of a group of ten channels on the same frequency, each one with their own unique pid number for audio and video??

I added a channel to the database manually.  The correct card was activated (DVB-S card), it moved the dish to the correct position, it got a lock on the signal (capital L in the OSD), but would not lock any video or audio (lowercase a and v in the OSD).  So, it was not finding them automatically during my test.  Telling it which APID and VPID to grab out of the stream seems like what is missing here for me.

---

