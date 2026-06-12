---
title: "Audacious 2 broken after upgrade to Lucid"
date: 2010-05-01
forum: Multimedia Software
---

### Post by Román on 2010-05-01
Hi, I just upgraded to lucid and the most noticeable change I got is that audacious no longer works.  It doesn't even start.:

```
rgoro@exopotamia:~$ audacious
audacious: symbol lookup error: audacious: undefined symbol: index_new
rgoro@exopotamia:~$ which audacious
/usr/bin/audacious
rgoro@exopotamia:~$ ls -l $(which audacious)
lrwxrwxrwx 1 root root 10 2010-05-01 11:02 /usr/bin/audacious -> audacious2
rgoro@exopotamia:~$ ls -l $(which audacious2)
-rwxr-xr-x 1 root root 552104 2010-04-22 16:40 /usr/bin/audacious2
rgoro@exopotamia:~$ audacious --version
Audacious 2.3 [Ubuntu package]
```I tried uninstalling and reinstalling, without success. I also googled the error message, but all I got was an old bug report in a SUSE forum, which didn't seem to solve anything.  

Attached is the log output (from "audacious -N") and the strace output (from "strace audacious").  I can't make heads or tails out of it.

---

