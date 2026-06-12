---
title: "how to submit mythbuntu theme music ui tweak"
date: 2010-02-07
forum: Mythbuntu
---

### Post by kja999 on 2010-02-07
Hi, 

I have altered the mythbuntu the file for music-ui.xml to show the star ratings for a track.
Its a tiny change (code was mostly there), but where/how should I request inclusion?

Also, as i am using packages not source, would I really need a diff file?


for those interested, the file is attached, and changes start at line 254 for that one section.

---

### Post by superm1 on 2010-02-07
Hi kja99:

The best way to get this included is to submit it to the MythTV bug tracker at [http://svn.mythtv.org](http://svn.mythtv.org).

Submit it in the form of a unified diff attached to a new bug report.  You can create a unified diff by backing up the original file, and then running this command (of course substituting file names):

```
diff -u file.orig file.new
```

---

### Post by kja999 on 2010-02-07
Thanks, couldn't be simpler ! ;)

---

