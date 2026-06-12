---
title: "Editing Metadata for Recordings ?"
date: 2010-11-25
forum: Mythbuntu
---

### Post by OmahaVike on 2010-11-25
Hello,

I dump all of my movies into Recordings.  Some movie art comes up, and others do not.  I'd like to edit the metadata on these files to match the lookup in TMDB, but I cannot figure out how to do it through the interface.

Some of my web searches have instructed the user to highlight the file in question, then press "i" and then go on to edit the metadata.  For these files, when I press "i", I only see file description information -- no further menu possible.

Other web searches indicate to highlight the file, then press "m".  This results in a menu with options "play", "add to playlist", "mark as watched", etc. none of which have any sub-option for metadata.

----
mythtvfrontend --version yields:

mythtv version:  24158
branch:  branches/release-0-23-fixes
library api:  0.23.20100314-1
----

I'd be very thankful if someone could help me find the metadata editing interface for recordings.

---

### Post by LowSky on 2010-11-25
you should have placed movies of your own into videos not recordings

thats why you're having issues

---

### Post by OmahaVike on 2010-11-25
unless there is a way of putting videos into categories, like recording groups, i won't move them over to videos.

i guess i'll go hack the database...  thanks!

---

### Post by alsalgado on 2010-11-25
I'm sorry if you're talking nonsense, but for me to edit the file I select and press E.
Sorry bad english.

---

### Post by OmahaVike on 2010-11-26
solution:  since i required to have them categorized, i left them in recordings.  to solve my problem, i went into the database and set the titles of the recordings exactly as they were in TMDB (themoviedb.org).  Then, i also found that some of the subtitles were named the same as the file, so I wiped those out.  Finally, ran mythvideo script and all was well.

Next up:  find out how to discriminate between movie titles that are remakes and have the exact title as a predecessor.

---

### Post by Senkoboy on 2010-11-27
> **alsalgado said:**
> I'm sorry if you're talking nonsense, but for me to edit the file I select and press E.
Sorry bad english.

That still won't let you edit the metadata on these files.

---

