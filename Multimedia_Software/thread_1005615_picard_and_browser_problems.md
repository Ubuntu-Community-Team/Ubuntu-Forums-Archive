---
title: "picard and browser problems"
date: 2008-12-08
forum: Multimedia Software
---

### Post by darrengoddard on 2008-12-08
i've recently reverted from flock back to firefox as my browser of choice.

all was well until today when i kicked off picard.  when i clicked on 'look up' nothing happened at all.  

i did some investigating and came up with this error:  

Error showing url: Failed to execute child process "/usr/share/flock/flock-browser" (No such file or directory)

it appears as though picard wants to start flock when flock is no longer there to be started.

how can i change the picard preferences to point it towards firefox instead?

your anticipated help is greatly appreciated.

---

### Post by darrengoddard on 2008-12-10
solved my own problem but thought i'd post the solution for anyone else...

system->preferences->preferred applications
internet tab (change back to firefox)

and that's it.

is it me or are most solutions pretty straight forward?

dg

---

