---
title: "Digikam 2.4.1 crash on start"
date: 2011-12-30
forum: Multimedia Software
---

### Post by wagoner on 2011-12-30
Digikam 2.1 wouldn't import from my camera, but it would work otherwise.

I updated to digikam 2.4.1 from a ppa I found in this thread.
[this thread]("http://ubuntuforums.org/showthread.php?t=1869192&highlight=digikam+ptp")

Now digikam crashes on start up.  In the terminal I get this error.
```
QSqlDatabasePrivate::removeDatabase: connection 'ConnectionTest' is still in use, all queries will cease to work.
digikam: symbol lookup error: digikam: undefined symbol: _ZN4KIPI21ImageCollectionSharedD2Ev

```

I've used digikam in the past, but it won't import from my camera since I upgraded several months ago.  Any suggestions on how to fix it now?  Wait for the next update?

---

### Post by wagoner on 2012-01-08
Looks like digikam 2.2.5.0 is now out for oneric.  Has anyone installed this?  I am thinking about trying it out.

---

### Post by llelectronics on 2012-01-08
I have it running here. It is running fine so far. (I think you meant 2.5.0) 
Sadly I don't know if it will fix your problem as it looks like a database error in your image collection. Maybe try deleting your database file and reindex your images would help.

---

