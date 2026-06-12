---
title: "mythshutdown locked - can't unlock it!"
date: 2010-09-22
forum: Mythbuntu
---

### Post by jonnybignote on 2010-09-22
9.10 64 bit

Hi all
most bizarre experience with this and, unless I'm missing something incredibly obvious, then I don't this I've come across it before.  I've done much searching and haven't seen this mentioned anywhere.

Quick background.
I'm using mythwelcome in my efforts to have the machine standby and resume which has been working great.  

I run certain programs - terminal etc - in shell scripts with mythshutdown -l and a while loop to keep the system locked and on while I work, releasing it with mythshutdown -u when done.  I also have keyboard shortcuts that can lock and unlock when needed.

Pretty standard stuff.

After a few days trying to fix some things,  I noticed yesterday that the machine is not unlocking and therefore permanently on.  No other programs are running, the machine has been rebooted and I fsck'd the hell out of it.

Whether invoking from terminal or from the mythwelcome menu, mythshutdown stays locked and I don't know what to do but leave it running so things get recorded....

Any help would be much appreciated.  I'm wondering if there is a rogue mythshutdown lock file or something though I have looked for the obvious things

Thanks

---

### Post by Neon Dusk on 2010-09-22
Mythshutdown keeps a counter with the number of times it's been locked in the database. Each time you run mythshutdown -l the counter increments and then decrements with mythshutdown -u.

It sounds as if the number of lock / unlock command you've ran are out of sync.

To clear all the locks a simple script like
```

#!/bin/bash

mask=16
mythshutdown --status
status=$?

while (($status & $mask))
do
        mythshutdown --unlock
        mythshutdown --status
        status=$?
done

```
should fix it.

---

### Post by jonnybignote on 2010-09-22
Thanks a lot for the help - I really appreciate it.  I get this output after running that:

```
mediapc@Hughes-MediaPC:~$ sudo sh fix_mythshutdown 
fix_mythshutdown: 12: mask: not found
mediapc@Hughes-MediaPC:~$ status: missing job name
Try `status --help' for more information.
```

after that, it doesn't complete, but hangs there.  

Sorry, if I understood code better, I'd try and resolve that myself

Thanks again

---

### Post by Neon Dusk on 2010-09-23
it's a bash script (in Ubuntu sh links to dash)

You should be able to run the script with
```

./fix_mythshutdown

```

---

### Post by jonnybignote on 2010-09-23
OK

Duly noted - thanks.

Formatting the command as above does give the same result unfortunately, with the following line:


```
./fix_mythshutdown: line 12:  3557 Segmentation fault      mythshutdown --unlock
```

It then stays open and continues to try while displaying the previous line every minute or so.

Thanks again

---

### Post by Neon Dusk on 2010-09-23
Do you get a segmentation fault when you run the command 'mythshutdown --unlock' ?

---

### Post by jonnybignote on 2010-09-23
So you're a genius! - thanks for fixing this for me.

I don't get the segmentation fault running lock or unlock, they both have been working fine for over a year.  It was the running of the script only that listed a segmentation fault.

Then it occurred to me that, while not really understanding your script, I did wonder whether I was supposed to do anything while it was running...so I did a few lock/unlock commands in the background while your script was running and hey presto!  The script completed and my machine was unlocked.

I don't pretend to understand what happened exactly but I'm good to go now - can't thank you enough!

Many thanks again

---

