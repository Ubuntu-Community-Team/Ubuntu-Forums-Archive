---
title: "via epia cn1000eg and HDHomeRun as backend?"
date: 2009-10-25
forum: Mythbuntu
---

### Post by minchina on 2009-10-25
Sorry for another hardware question, but I am just dipping my toe in mythbuntu and I want to see if I understand what I am getting into.

I have a via epia cn1000eg that I want to pair with an HDHomeRun as a backend.  I know that the via board is not very powerful.  My vision is to use the via board to record the HDHomeRun MPEG2 stream (at this point it is easier to get a big drive than a faster chip to encode the stream).  I will pair my backend with some other solution - maybe this Asus Eee Box ([http://www.netbookreviews.net/asus/eb1501-hands-on/](http://www.netbookreviews.net/asus/eb1501-hands-on/)) - that can handle the HD decoding and will be hooked up to the TV.

Will my litle via board be able to handle what I throw at it as a back end?  In my mind it is only acting as a server and to schedule recording, which it should not have a problem handling (I think - streaming isn't very cycle intensive, is it?).  However, I am afraid that I am missing some important function that will sink the project.  Does anyone have any ideas?  I know that traditionally it is the backend that has the power and the frontend that is lightweight, but this setup seems to make sense to me.  Am I crazy to do this, or crazy like a fox?

thanks

---

### Post by ian dobson on 2009-10-26
Hi,

That via box should be enough for a simple backend. Actually recording/streaming video doesn't need that much CPU. 

I'm not sure how it would cope with commercial flagging/transcoding but you could limit the backend to only one job at a time. Just make sure you have enough ram in the backend the more ram you have the better linux can cache data rather than trying to get it from the harddisk all the time.

On my "overpowered" backend (Q9550, 6Tb RAID 5 array, 8Gb ram) I can record 4 HD and 2 SD streams at the same time with almost no CPU load.

Regards
Ian Dobson

---

### Post by minchina on 2009-10-31
Thanks for the answer.  Does the back end have to transcode?  I'm happy to store everything in MPEG2 if that takes the load off of the CPU

---

### Post by ian dobson on 2009-11-01
Hi,

No the backend doesn't have to transcode, you can store the files a mpeg2. But commflagging (commercial flagging) should be left enabled, for me thats one of the best features in MythTV.

Regards
Ian Dobson

---

