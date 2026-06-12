---
title: "[SOLVED] Can't delete shows!"
date: 2008-08-09
forum: Mythbuntu
---

### Post by yonkiman on 2008-08-09
For some reason I can't delete some shows.  I delete them, they disappear from the stored shows menu, then they come back 5 seconds later.  I've looked at the storage options settings and they all seem normal (none of them are set to don't delete, etc.).

Any ideas?  Using 8.04.1.  Never had this problem with 8.04 - maybe it's something in the new version?  But I don't see anyone else complaining...

---

### Post by newlinux on 2008-08-10
what's in your backend logs when you try to delete a show? do the files actually exist in your recordings directory?

---

### Post by yonkiman on 2008-08-10
> **newlinux said:**
> what's in your backend logs when you try to delete a show?

```
2008-08-10 14:27:29.511 Error deleting '/var/lib/mythtv/recordings/1009_20080801200000.mpg' could not open 
			eno: Permission denied (13)
2008-08-10 14:27:29.517 Delete Error '/var/lib/mythtv/recordings/1009_20080801200000.mpg'
			eno: Permission denied (13)
2008-08-10 14:27:29.518 Error deleting file: /var/lib/mythtv/recordings/1009_20080801200000.mpg. Keeping metadata in database.

```
> do the files actually exist in your recordings directory?

Yes, they are in the default /var/lib/mythtv/recordings directory.

So apparently I did something around August 2nd that changed the owner and the file permissions of the recorded files.  Here is the recordings directory around August 2:
```
-rw-r--r-- 1 mythtv mythtv  2385178800 2008-08-04 22:00 1037_20080804210000.mpg
-rw-r--r-- 1 mythtv mythtv  1211083304 2008-08-04 19:00 1063_20080804183000.mpg
-rw-r--r-- 1 mythtv mythtv 19499323528 2008-08-03 18:00 2091_20080803133000.mpg
-rw-r--r-- 1 root   mythtv    39976508 2008-08-02 06:57 2543_20080725233000.mpg
-rw-r--r-- 1 root   mythtv   761382704 2008-08-02 06:57 2543_20080718233000.mpg

```
I think that "something" was "transferring my library from my old 8.04 machine to my new 8.04.1 machine".  All the newer files delete fine.  So I'll just change the permissions on these files and chalk it up to the database transfer.

Thanks for pointing me in the right direction!

---

