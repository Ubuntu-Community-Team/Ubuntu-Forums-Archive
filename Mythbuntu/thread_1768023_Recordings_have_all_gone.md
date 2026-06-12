---
title: "Recordings have all gone"
date: 2011-05-26
forum: Mythbuntu
---

### Post by Billsputters on 2011-05-26
I've had a good route around and can't find anything relevant to this.

I've lost all my recordings! They are there, MythWeb says so. But the FE shows a blank on Recordings, and the same if I do the same at the BE.

I have not rebooted, for fear of doing causing permanent amnesia with MythTV.

Needless to say, everything was working well and happy since February, so am at a loss. I can view Videos and play music, so there is a connection there, and LiveTV works. Just can't see my recordings, and I want to know what happens in Dr. Who!

---

### Post by klc5555 on 2011-05-26
Well, you still have your actual recordings and you have of course been doing your daily and weekly database backups (right?) so you would have an array of dated database backups in case something completely fried your current database. (The database is likely not fried).

Sometimes these little database access glitches can be solved simply by stopping and restarting the master backend. If not, frequently a reboot of the master backend machine solves the backend's glitch in properly accessing the database.

If this doesn't solve the issue, because there is some small corruption one or more database tables, the next option might be to run the mysql optimize utilities from mythbuntu control center or, in the presence of greater corruption, to run mysqlcheck --auto-repair from a prompt (Read the man page for mysqlcheck).

But if the database turned out not to be repairable, you'd likely  do a restore from your most recent daily backup.

And finally, if you didn't happen to have a database backup, it appears (since myth.rebuilddatabase.pl is now defunct, like most useful things from earlier versions of mythtv) you're supposed to dump all your now anonymous tv recordings files into mythvideo and play them from there. At least according to the wiki stub that remains of the old myth.rebuilddatabase.pl page. at wiki.mythtv.org

There may well be other options too, but these are the ones I've used from time to time (well, except for the mythvideo one).

---

### Post by nickrout on 2011-05-26
make sure you haven't filtered the recordings you are watching.

---

