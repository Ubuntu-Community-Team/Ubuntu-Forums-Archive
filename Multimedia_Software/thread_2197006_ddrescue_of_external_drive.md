---
title: "ddrescue of external drive"
date: 2014-01-01
forum: Multimedia Software
---

### Post by zenmatrix on 2014-01-01
I have an external drive I stored movies on that started to fail and the partition is damaged to the point I can't access it normally. Some of these haven't been backed up yet and are quite important. I was able to restore some using photorec but started getting alot more errors reading sectors. I have ddrescue started on it using just the -S for it to create a sparse file. I need to do that because its a 2tb drive with only about 250gb of data and I can't afford another drive right now. What is the best command to run with ddrescue to run on a dying drive?

---

### Post by zenmatrix on 2014-01-01
right now I'm averaging 166 kb/s  heres the output

root@ubuntu:/home/stephen/movies# ddrescue -S /dev/sdc drive recovery.log


GNU ddrescue 1.16
Press Ctrl-C to interrupt
rescued:     1069 MB,  errsize:    278 MB,  current rate:     196 kB/s
   ipos:     1348 MB,   errors:       8,    average rate:     165 kB/s
   opos:     1348 MB,     time since last successful read:       0 s
Copying non-tried blocks...

Copying non-tried blocks...

---

### Post by sudodus on 2014-01-04
When a drive is failing you should not run it at all except to make a backup clone (with ddrescue and make a log file at the same time). Please read info page ```
info ddrescue
``` carefully.

So if you cannot buy the backup drive now, wait, and let the failing drive rest until you can make the backup clone

---

