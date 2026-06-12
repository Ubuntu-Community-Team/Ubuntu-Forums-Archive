---
title: "Recordings saved with incorrect timestamp"
date: 2014-08-23
forum: Mythbuntu
---

### Post by wylie982 on 2014-08-23
Hi All,

I have just upgraded from 12.04 to 14.04/MythTV0.27. Although everything works fine, I have noticed a weirdness in the way Mythtv names recorded files now. I live in Denmark and although my recordings start and stop at the right time and the time, and the guide data is displayed with the correct time offset, the saved files are named with the incorrect time. So a file recorded at 2100 wich should have a file name like 1002_20140822210000 ends up 1002_20140822190000. This means that when I use a script to reencode them the file names don't match the %STARTTIME% that the user job parses.

Any help

Chris

---

### Post by khPWXxF on 2014-08-23
Here in the UK recording names are one hour out.  It seems the recordings now have a UTC timestamp not local time in the name.
See 
 [http://www.mythtv.org/wiki/User_Jobs](http://www.mythtv.org/wiki/User_Jobs)

Will using %STARTTIMEUTC% do what you want?
Phil

---

