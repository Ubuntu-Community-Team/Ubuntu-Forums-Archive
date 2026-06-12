---
title: "Backup up database before clean reinstall: which tables?"
date: 2009-12-27
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-12-27
I'm about to upgrade my Mythbuntu 8.10 system to 9.10 by doing a clean reinstall.

I've figured out how to back up and restore my database, but after reading various posts such as [this one]("http://ubuntuforums.org/showthread.php?t=1292030&page=2"), I'm now wondering whether it's sensible to restore my entire database or just a few tables from it.

I have a photo collection, a music collection, some videos, and many TV recordings, and would like them all to be accessible just as they were before the upgrade, and for the TV recording scheduler to know which programmes I've already told it to record.

I'm not too keen on having all my configuration settings remembered, as part of the reason for doing a clean install is that I never really knew what I was doing before, and I suspect I'd do a much better job of setting everything up the second time around.

I guess I'm a bit confused about what exactly is in the database.

Any thoughts that would help me to decide whether to restore the whole database or just selected tables, and if the latter, which tables, would be gratefully received!

Thanks
NM

---

### Post by ubnewbie2 on 2009-12-27
I just did this earlier today.  I restored the whole database.  There's a bunch of stuff that needs to be redone after the database upgrades.  For example, I had to re-add each of the tuner cards.  Lot's of settings seemed slightly different, so I ended up revisiting all the setup.  However, all my shows and recording schedules, videos, etc etc, all came across quite well.

---

### Post by Yasire on 2009-12-27
I would recommend backing up pretty much everything - there's not too much junk to worry about in there.  And I suspect you want that data, such as previously recorded episodes.  

Speaking of which, I've been using MythTV .18 under Fedora for the last few years (about 4 years with this box?).  Never did any upgrades.  Now, I'm thinking it's time to switch to Mythbuntu.  Seeing as they are both running Myth, can I backup/restore databases?  Or are they drastically different between Mythtv .18 and latest (is it .22 latest?)

---

### Post by uncle hammy on 2009-12-27
> **Yasire said:**
> I would recommend backing up pretty much everything - there's not too much junk to worry about in there.  And I suspect you want that data, such as previously recorded episodes.  

Speaking of which, I've been using MythTV .18 under Fedora for the last few years (about 4 years with this box?).  Never did any upgrades.  Now, I'm thinking it's time to switch to Mythbuntu.  Seeing as they are both running Myth, can I backup/restore databases?  Or are they drastically different between Mythtv .18 and latest (is it .22 latest?)

The database schemas are drastically different from .18 to .22.  There were upgrade processes along the way to take care of it.  I am not entirely sure what sort of path you would have to take to go from .18 to .22 and maintain your data at this point.  Not saying it can't be done...I just don't know what the process would be.

---

### Post by nickrout on 2009-12-27
The steps are well documented here:

[http://www.gossamer-threads.com/lists/mythtv/users/405443](http://www.gossamer-threads.com/lists/mythtv/users/405443)

---

### Post by NautiusMaximus on 2009-12-28
OK, I've done it, and I restored the whole database. Doesn't seem to have caused any major problems, and all my TV programmes are still there. Hooray!

---

### Post by ubnewbie2 on 2009-12-28
> **NautiusMaximus said:**
> OK, I've done it, and I restored the whole database. Doesn't seem to have caused any major problems, and all my TV programmes are still there. Hooray!

Yeah I was very happy to see all the stuff still there and working too. Congrats.

---

