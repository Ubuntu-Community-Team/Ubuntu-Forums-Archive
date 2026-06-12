---
title: "Transcoding not Changing File"
date: 2008-09-23
forum: Mythbuntu
---

### Post by Ronno6 on 2008-09-23
I've configured my Mythbuntu 8.04.1 according to the post 
[http://ubuntuforums.org/showthread.php?t=346778](http://ubuntuforums.org/showthread.php?t=346778)

I've set transcoder profiles to   "Lossless Transcoding" 

Commercial flagging is enabled and run. Segments are indicated.

Transcoding my recordings does not alter the file size, and flagged commercial segments are still present.

What should I check to correct this?

---

### Post by anonymousdog on 2008-09-23
That guide looks old.  Try the stuff [here](http://www.mythtv.org/wiki/index.php/Script_-_RemoveCommercials).  I've got some scripts you can use if you like that incorporate nearly all of the improvements posted piece meal on that page and the discussion tab plus some improvements to the "cleanup" of the sql database.  PM me if you want them.

---

### Post by Ronno6 on 2008-09-23
Thanks for the input. I will try that shortly. In the mean time I've found that transcode only removes commercial breaks if I manually mark the them. It ignores anything automatically flagged, even though the segments are skipped during playback.
As I am still learning the ways of Ubuntu, how would I get your suggested User Job? Would that be a copy and paste? To what directory?
Thank you again.

---

### Post by anonymousdog on 2008-09-23
Yep.  It's looking for a cutlist, not commercial flags.  The easiest way I've found to make a cutlist is to edit the recording while watching it.  You can instantly convert all commflags to a cutlist by pressing the End (or Z) key while editing.  From there it's a little easier to just clean up any mistakes or omissions than to manually create a cutlist.

I can send you an archive of the scripts.  You extract the scripts to a directory like /usr/local/bin and ensure your mythbackend account, mythtv by default, has rx permissions on them.  Then you add the scripts and arguments as user jobs in mythbackend setup (or via mythweb).  See [here](http://www.mythtv.org/wiki/index.php/Removing_Commercials#Automatically_removing_commercials) for an overview.  As with most things, they are a work in progress and can be improved.  I have a handful of scripts I think I can reduce to two, but I'm pretty happy with them for now.

---

### Post by SiHa on 2008-09-24
I could use those scripts as well, if I pm you with my email address, could you send them to me? I'm just about to embark on the brave new world of Transcoding, and anything that makes it easier has got to be a good thing.
TIA,
Simon

---

### Post by klc5555 on 2008-09-24
> **anonymousdog said:**
> That guide looks old.  Try the stuff [here](http://www.mythtv.org/wiki/index.php/Script_-_RemoveCommercials).  


I believe that this script "as is" should only work properly with recordings from analog sources, since "mythcommflag --rebuild"  seems to produce unusable seek tables when applied to recordings from DVB sources.  For recordings from digital sources one generally needs to use "mythtranscode --mpeg2 --buildindex" along with the -i or the -c and -s switches.

All the best.

---

### Post by anonymousdog on 2008-09-24
> **klc5555 said:**
> I believe that this script "as is" should only work properly with recordings from analog sources, since "mythcommflag --rebuild"  seems to produce unusable seek tables when applied to recordings from DVB sources.  For recordings from digital sources one generally needs to use "mythtranscode --mpeg2 --buildindex" along with the -i or the -c and -s switches.

FWIW, I had very bad outcomes using mythcommflag --rebuild for analog sourced recordings too; so the scripts all use mythtranscode --mpeg2 --buildindex --allkeys.

That said, I've not tested them on DVB sourced recordings.  I'll post 'em tonight.

---

### Post by anonymousdog on 2008-09-25
This script, remove_commercials, takes several argument variables that mythbackend successfully provides.  It also takes a final, optional argument, "SKIP", so that it can be run two ways: with or without a pre-existing cutlist for the recording.

Make sure its permissions are at least rx for the mythtv-backend service account, mythtv in Mythbuntu, once you've extracted it.

The command line to put into mythbackend setup, user jobs list would be```
<path-to-script>/remove_commercials  %DIR% "%FILE%" %CHANID% %STARTTIME%
```to remove commercials in a single step from a virgin recording file.

Another user job might be to "SKIP" the cutlist generation and original recording backup but remove commercials from a recording that already has a cutlist.```
<path-to-script>/remove_commercials  %DIR% "%FILE%" %CHANID% %STARTTIME% 'SKIP'
```Yep, just add 'SKIP' as the last argument, and commflagging, generating the cutlist and backup of the original file will be skipped.

I've never gotten backend jobs that run mysql client to successfully login without supplying the credentials in the script.  So, you'll have to edit the script near the end either to include your mythconverg password or to strip out the password option entirely.

It would be trivial to create a "delete original" script to compliment the skipless option in remove_commercials.  Running that script without 'SKIP' does use up storage at approximately %170 or the original recording size.  So, you also want MythTV to reserve enough space on your file system to accomodate more than ~70% of your largest expected recording size (in order not to run out of room while processing remove_commercials).

---

### Post by anonymousdog on 2008-09-25
The "other scripts" all have the same skeletal structure; so, they can likely be combined with remove_commercials if better argument parsing can be coded.

undo_remove_commercials takes the same arguments (with the exception of 'SKIP').  It restores the backed up original for recordings where you ran the remove_commercials job without 'SKIP' (so a backup of the original is available).

remove_all_markup takes the same four argurments.  It takes a recording with a horked seeklist or filesize entries in the database and fixes the database to reflect the file.  It leaves no commflagging data, and no cutlist: No markup but for a fresh seeklist.

---

### Post by Ronno6 on 2008-09-25
Thanks, AD. I'll be working on it !

---

### Post by anonymousdog on 2008-09-25
Feel free to hit the "thanks" button below. ;-)

---

