---
title: "Add User Job mythlink.pl"
date: 2012-10-01
forum: Mythbuntu
---

### Post by k7_madman on 2012-10-01
I would like my recordings to have human readable names.  I have read that the mythlink.pl script can do this. But I am not sure how to implement it.  I would like it to run after every recording, and I want the format to be [title]-[subtitle]. Do I just add this mythweb interface under UserJob1?  Do I need the full script path?  Any help will be greatly appreciated.

I have set the script to executable.
/usr/share/doc/mythtv-backend/contrib/user_jobs$ sudo chmod a+x mythlink.pl


mythlink.pl --link /var/lib/mythtv/recordings --format '%T-%S'

---

### Post by nickrout on 2012-10-01
> **k7_madman said:**
> I would like my recordings to have human readable names.  I have read that the mythlink.pl script can do this. But I am not sure how to implement it.  I would like it to run after every recording, and I want the format to be [title]-[subtitle]. Do I just add this mythweb interface under UserJob1?  Do I need the full script path?  Any help will be greatly appreciated.

I have set the script to executable.
/usr/share/doc/mythtv-backend/contrib/user_jobs$ sudo chmod a+x mythlink.pl


mythlink.pl --link /var/lib/mythtv/recordings --format '%T-%S'

You are better to run this via the system event manager use the "on recording start" event.

Also you want to put the symlinks in ANOTHER directory, like /var/lib/mythtv/pretty - that leaves the originals intact, which is important!

[http://www.mythtv.org/wiki/Mythlink.pl#Using_with_MythTV_System_Events](http://www.mythtv.org/wiki/Mythlink.pl#Using_with_MythTV_System_Events)

---

### Post by k7_madman on 2012-10-06
OK, I think I got the correct format command.  I tested it and the output looks good.  I guess my real question is how do I implement this....do I just make a cronjob for this?...or do I have to have it add as a userjob in mythtv itself.



/usr/share/doc/mythtv-backend/contrib/user_jobs/mythlink.pl --link /var/lib/mythtv/videos --format '%T-%S'

---

### Post by nickrout on 2012-10-06
No you need to read the link I gave you.

---

