---
title: "Hash sum Mismatch from extras.ubuntu.com"
date: 2010-10-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Lolpanda on 2010-10-08
Title says it, google has only turned up one ubuntuforum post from 6.04 so I new thread is made. 

Anytime I update apt (commandline or synaptic) it fails when pulling sources.bz2 from 

[http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.bz2)

and

[http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.bz2)


If they aren't live yet thats fine. At first I was just like "Oh must've caught them during an update, no biggie" so I let it go for 24hrs, but today its the same deal still. Tried changing my sources from The US server to the main server and the "Choose best server" just incase it had anything to do with it, and all of them said the same thing -- hash sum mismatch.

LIke I said, google's only turned up one post about this, and it was for 6.04 not 10.10 so it wasnt much help.

---

### Post by wgrant on 2010-10-09
We fixed this a couple of hours ago. Can you try again?

---

### Post by Lolpanda on 2010-10-09
Seems to be working now, thanks :D Only warnings im getting are for the ppa's I added prematurely and those'll prob be fixed on or around sunday.

thanks for the update wgrant

---

### Post by vaskark on 2010-10-09
The extras repo hasn't been added to my sources.list file yet. Can someone post it so I can add it manually?

---

### Post by howefield on 2010-10-09
> **vaskark said:**
> The extras repo hasn't been added to my sources.list file yet. Can someone post it so I can add it manually?

This is what is in mine.

```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
```

---

### Post by vaskark on 2010-10-09
Many thanks.

---

