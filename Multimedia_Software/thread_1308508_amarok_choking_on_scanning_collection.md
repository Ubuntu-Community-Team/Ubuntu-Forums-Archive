---
title: "amarok choking on scanning collection"
date: 2009-10-31
forum: Multimedia Software
---

### Post by kjkrum on 2009-10-31
Amarok is choking on scanning my music collection.  Tailing its scan logs reveals that all files are being scanned, and removing the last file scanned does not fix the problem.  It hangs *after* scanning files.

While it's hung, it uses all available CPU cycles (80-97% according to top).  If only a few files are scanned, it grinds for only a fraction of a second.  If about 600 files are scanned, it grinds for about 30 seconds.  With all 2400+ files in my collection, it never finishes.  (Well, I killed it after 20 minutes.)

I tried using mysql instead of the built-in database.  This time it finished scanning my collection after about 10 minutes.  Amarok 1.4 scans the same files in just a few seconds.

Any ideas?

Edit: It seems to depend not on the number of songs in the collection, but on the number of files in any given directory.

My Amarok is watching two directories.  After finally getting all 2400+ files in the main directory scanned in, I added one file to the empty directory and rescanned the collection.  The scanning process took only a second or two, and the file was added to the collection.

I then moved the same new file to the main directory with 2400+ other files and rescanned the collection.  It again did something CPU-bound for several minutes after scanning the files.

I tried letting it organize the files into subdirectories and repeating the experiment.  The results were the same.

---

