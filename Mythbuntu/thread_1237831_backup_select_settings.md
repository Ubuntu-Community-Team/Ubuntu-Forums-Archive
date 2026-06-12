---
title: "backup select settings"
date: 2009-08-11
forum: Mythbuntu
---

### Post by usmcstitch on 2009-08-11
I have borked up my Mythbuntu install in some form or fashion.  Missing Sream Icon, Video browsing/meta data not working correctly (crashing the frontend), Weather just giving a blank screen and a few other issues here and there.  basically, since i'm not TOO far into it, i'd like to just kill it and start over.

However....I have the TV the way i like it, with the guide data inputed and channels mapped the way i want, icons where they need to be etc.  TV is the only thing that works (sometimes!  i get a blank screen and the return to menu at random points).  

Question:  Is there a way to just backup the TV settings?  I really don't want to have to redo all the channels AGAIN (would be 5th time, its not as fun as you'd think).

I'm using Mythbuntu 9.04 x64.  Should i be using an earlier version?

---

### Post by Caysho on 2009-08-11
Yes, just back up the specific tables with phpmyadmin.
The [mythtv schema]("http://www.mythtv.org/wiki/Database_Schema") should provide some guidance.
Or you can connect to the MySQL backend and export them from there :)

---

### Post by usmcstitch on 2009-08-11
I'm a pretty nooblet novice when it comes to databases and using phpmyadmin.  EDIT:  SNIP all the junk.

These are the tables i am pulling:
callsignnetworkmap
capturecard
cardinput
channel
tvchain.

I don't have recordings, all i need is my Source, tuner, channel info.  Did i miss anything?

thx for the asist.

---

### Post by mitchell2345 on 2009-08-12
what is your source?

If you are recording Digital TV you will need DTV_multiplex.

~Mitchell

---

