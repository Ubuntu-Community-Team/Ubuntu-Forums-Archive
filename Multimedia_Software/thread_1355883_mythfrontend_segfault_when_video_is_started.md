---
title: "mythfrontend segfault when video is started"
date: 2009-12-15
forum: Multimedia Software
---

### Post by klavsk on 2009-12-15
I've just installed mythbuntu 9.10 on a dual-core atom (asus eee box 1012) with nvidia graphics.

Whenever I run mythfrontend (against my mythbackend on another box), and start "watch video" (or "video manager" - under "utilities / setup") mythfrontend segmentation faults. 

There's nothing listed in the logs :(

I have mythfrontend on other machines(not running *buntu 9.10, using the same backend) and they all work fine.

Since the machine is completely vanilla, I figured someone else should have seen this issue as well, but I can't find any posts that seem to match.

Any hints or ideas as to what I could try?

I tried running mythfrontend -v all >/tmp/debug and the output shows nothing relevant it seems:
[http://vsen.dk/files/mythfrontend-debug](http://vsen.dk/files/mythfrontend-debug)

p.s. the movies folder is an nfs mount to the backend - but I haven't even gotten to configure the mythvideo setup - as it dies when trying that as well.

---

### Post by diamaunt on 2009-12-29
My second front end was doing the same thing.  I did the same trace you suggested, and mine died right after it did a select data from settings where value = "VideoStartupDir" and hostname = NULL; 

I popped into mysql and did that same select, and got back nothing, (before that, it'd tried a select with it's hostname, which also wasn't in the file.

so, I inserted a row into the settings table with VideoStartupDir, the correct dir,NULL. and it worked fine after that.  

INSERT INTO `mythconverg`.`settings` (`value`, `data`, `hostname`) VALUES ('VideoStartupDir', '/mythtv/vid', NULL);

in my case.

hth, cheers!

---

