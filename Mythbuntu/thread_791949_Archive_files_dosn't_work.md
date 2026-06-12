---
title: "Archive files dosn't work"
date: 2008-05-12
forum: Mythbuntu
---

### Post by thusgaard on 2008-05-12
Hi 

I can not burn DVD's or make ISO files with the Archive Option under "optical disks". I choose the show I want on DVD, and nothing happens. Can any one tell me how to do this right?

J;-)

---

### Post by jakev383 on 2008-05-12
Did you set up the correct paths in the Utils/Setup -> Setup -> Media Settings -> Archive Files Settings?

---

### Post by agamotto on 2008-05-12
> **jakev383 said:**
> Did you set up the correct paths in the Utils/Setup -> Setup -> Media Settings -> Archive Files Settings?

I am curious as well.  I just noticed, that after upgrading to 8.04, mine doesn't work either.  It claims during the dvdauthor phase that /dev/dvd doesn't exist?  I don't see how, as it worked exactly this way under 7.10.

Are we just missing something so simple it is obvious?

---

### Post by thusgaard on 2008-05-13
> **jakev383 said:**
> Did you set up the correct paths in the Utils/Setup -> Setup -> Media Settings -> Archive Files Settings?

Please specify which paths you think may be wrong. 

I've tried changing /dev/dvd to /dev/dvdrw and it didn't help. the rest of the paths is beyond my scope of knowledge.

J;-)

---

### Post by jakev383 on 2008-05-14
You'll need to find out what device your DVD burner actually is to burn to it.  Put a disk in and after it mounts, drop to a CLI and issue "mount" to see the currently mounted devices on your system.  On mine, the DVD drive (with a burned disk in it) shows as:
```
/dev/scd0 on /media/cdrom1 type iso9660 (ro,nosuid,nodev,user=jake)
```
So I know my DVD burner is at /dev/scd0.

When you select to make just an ISO and not burn the DVD, does it still fail?

---

### Post by thusgaard on 2008-05-14
> **jakev383 said:**
> 
When you select to make just an ISO and not burn the DVD, does it still fail?

Mine is also SCD0, but it still fails, even to start. 

Just an ISO is the same problem!

J;-)

---

### Post by agamotto on 2008-07-17
> **thusgaard said:**
> Mine is also SCD0, but it still fails, even to start. 

Just an ISO is the same problem!

J;-)

This may be related to another post in this forum that relates to a similar problem.  I just upgraded from 7.10 to 8.04.1, and no burning of dvds, with the same error you mention earlier.  There is a thread in this forum that mentions the .ICEauthority file.  The fix seems to be essentially to add a line to one of the start scripts, which will keep this file from being created.  Sorry I don't have the exact thread to give, but I am not that great with forum editing yet.  Search 'this forum' for .ICEauthority, and the solution may be there.  I have applied the 'fix,' and am currently running MythArchive to see if it spits out a finished DVD.

**Update:[B]I tried burning a DVD this morning with no luck.  So, I started another thread relating this problem to 8.04.1 to see if that helps in finding someone with a solution.**[/B]

---

### Post by A. J. Rimmer on 2008-07-25
> **thusgaard said:**
> Hi 

I can not burn DVD's or make ISO files with the Archive Option under "optical disks". I choose the show I want on DVD, and nothing happens. Can any one tell me how to do this right?

J;-)

OK, I just started using mytharchive today and ran into the exact problem you describe.  I did a little Googling and came up with this:

[http://www.mythtv.org/wiki/index.php/MythArchive#MythArchive_doesn.27t_work._It_gets_to_the_log_viewer_and_just_sits_there._What.27s_wrong.3F](http://www.mythtv.org/wiki/index.php/MythArchive#MythArchive_doesn.27t_work._It_gets_to_the_log_viewer_and_just_sits_there._What.27s_wrong.3F)

which basically says:

"This is also a symptom of an incorrect temporary files setting. Note that the user running mythfrontend needs write access in this directory, regardless of the user running mythbackend."

So I deleted the temporary directory I had created (I had to use root privilege to create it, duh) and made a new one in my home directory.  I made a test DVD and it worked great.  Right now I am making a DVD from a half-hour of HD video and it's taking a loooooong time!

(I should mention that I am using Gutsy Gibbon.)

---

