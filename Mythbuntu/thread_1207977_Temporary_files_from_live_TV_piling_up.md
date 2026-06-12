---
title: "Temporary files from live TV piling up"
date: 2009-07-08
forum: Mythbuntu
---

### Post by mathog on 2009-07-08
A couple of days ago the system had problems updating the EPG tables, and after trying a bunch of things, resetting the schedulesdirect password fixed it.  Now the EPG is up to date, but ever since then, it has stopped deleting the temporary files which are created while watching TV.  So one of the fixes for the first problem seems to have caused the second one.  To be honest I have never quite understood why these are kept a day (according to the setup -> tv settings -> general, livetvmaxage = 1 setting) when there seems to be no way to return to them once the program has completed, since they never appear in the list in "watch recordings".   That is, I guess, a separate question.  The main one now is, what could possibly be set so that all of these are retained in the data directory, apparently forever?

It MAY be that when we completely run out of space these will actually be removed, but in the meantime the "delete recordings" space indication shows only a few GB free.

Thanks.

---

### Post by mathog on 2009-07-08
Hmm, apparently this happened before, there were a pile of temporary live TV files left over from 6/17 and 6/23.

---

### Post by mathog on 2009-07-09
In the TV settings, playback section there are:

Default group filter to apply:  all programs
Show livetv recordings when using "all programs" filter

If the latter is checked all of the temporary shows are shown, but mixed in with the programmed recordings.  If it is not checked then the livetv entries are only supposed to show up in the "special livetv recording group", but there is no such entry on the list on the left, so no way to view these at all.  There is only one playback group listed in the setup, and that is "default".  I tried adding a "LiveTV" playback group, but after doing so, and watching some livetv, there was no corresponding entry in the playback list.

What am I missing???

---

### Post by crez79 on 2009-07-09
In the recordings list, hit 'm' and under filters, there is an option to show live tv group. If you check that and all programs like you have, it should take all the live tv that is mixed, and put it in a livetv group.

---

### Post by mathog on 2009-07-09
> **crez79 said:**
> In the recordings list, hit 'm' and under filters, there is an option to show live tv group. If you check that and all programs like you have, it should take all the live tv that is mixed, and put it in a livetv group.

That sort of worked.  I could get livetv onto the left side, but it also placed every program entry onto the same list.  I went through and deleted all the livetv entries.  It took a long time, as there were about 50 entries with no associated files, going back 5 months.  Ironically, if it couldn't find the data file it asked me twice if I wanted to delete the entry, rather than just once if the data file was there.  (As opposed to putting up a first menu when it can't find the file: "There is no file for this entry - delete?", or even better, "Multiple entries found without corresponding files, delete these?", at which point one click would have sufficed.)

What I really need is a "nuke all livetv entries after 1 day" that works completely - taking out the large data files as well as the database entries.

---

### Post by crez79 on 2009-07-09
Take a look at the myth.find_orphans.pl script. For me it is located in /usr/share/doc/mythtv-backend/contrib. It is supposed to find any recording that are in the database and not on the disk and recordings that are on the disk but not in the database and allow you to delete whichever one you want. 

It would be nice if it had the ability to find orphans on it's own, but that could pose a problem to those with more than one backend, or more than one storage location. I have multiple folders set up to save recordings and if for whatever reason one of them isn't mounted, myth just overlooks it. I don't want it to delete the database entries because the recordings do exist, just not right now. Myth doesn't know which folder a particular recording is in, it just knows the filename and where to look for it. It wouldn't be a good default behavior I don't think because a lot of people use multiple recording locations. It would make a good menu option in the system infromation section or something, but not an automatic thing.

---

