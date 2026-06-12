---
title: "Exaile collection count increases after every scan"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by noahsark1126 on 2008-03-06
I'm having a bit of a strange problem with Exaile.  It seems that every time my library is rescanned, the song count increases, which means that with it set to scan every 60 minutes, by the end of the day it can be several hundred over the real value.  After startup, it reads 3767 songs.  If I then tell it to rescan, in terminal I get 

```
Library rescan called
Running is False
File count: 3767
Created db for thread Thread-8
{'Thread-8': <sqlite3.Connection object at 0x92af5c0>}
Committing 1500 scanned tracks...
Committing 1500 scanned tracks...
Closed db for thread Thread-8
Count is now: 3767
```

but the count (in the actual Exaile window) now reads 3785.

If I call another rescan, the output is 

```
Library rescan called
Running is False
File count: 3767
Created db for thread Thread-10
{'Thread-10': <sqlite3.Connection object at 0x9ffd5c0>}
Committing 1500 scanned tracks...
Committing 1500 scanned tracks...
Closed db for thread Thread-10
Count is now: 3767
```

but the GUI says 3803.

Another call gives 

```
Library rescan called
Running is False
File count: 3767
Created db for thread Thread-12
{'Thread-12': <sqlite3.Connection object at 0xa0005c0>}
Committing 1500 scanned tracks...
Committing 1500 scanned tracks...
Closed db for thread Thread-12
Count is now: 3767

```

but the count is now 3821!!  And so on and so forth.

So, it seems that after every scan, the count increases by 18, even though the output in terminal seems to know the real number.  The only thing that seems to change in the backtrace is the line "Created db for thread Thread-8"...that number increases by 2 each time it is called.

Anyone have any idea what is going on here?

---

### Post by noahsark1126 on 2008-03-08
anyone??

---

### Post by imdano on 2008-03-08
You should report it to the exaile bug tracker: [https://launchpad.net/exaile](https://launchpad.net/exaile)

---

### Post by dashnak on 2008-03-08
Although many ubunters use exaile, this is not the place to ask about such a thing, you should try exaile's homepage or like imdano said, try the bug tracker.

---

### Post by olavjunior on 2008-05-24
EDIT: Have you tried a restart of Exaile? Then the number in the player gets updated to the correct value. (This is a minor bug)

---

