---
title: "mytharchive fail on dvd creation for videos"
date: 2010-01-03
forum: Mythbuntu
---

### Post by eljeffe on 2010-01-03
I have a local folder ~/Videos and my recordings are stored in a storage group. Since I am using a combined front and back end, all files are on the local file system. I also use the mythrename.pl script to put human readable links to all my recordings.

When I try to create a dvd from recordings the process is successful. 

When I try to create a dvd from either the links to recordings, or files in my ~/Videos directory, it fails.
 [INDENT]ERROR: Waited too long for mythtranscode to create the fifos
***********************************************
chmod: changing permissions of '/var/log/mytharchive/temp/': Operation not permitted[/INDENT]

When I go to the temp dirs there are files that are owned by mythtv, but also files owned by me.

---

### Post by eljeffe on 2010-01-03
Oops. That's not the issue, I have lots of problems with this feature, but it does not seem to be related to the location of the files. I'll try to do some better repro work and post it.

---

