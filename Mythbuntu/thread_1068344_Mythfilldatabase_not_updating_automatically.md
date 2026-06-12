---
title: "Mythfilldatabase not updating automatically"
date: 2009-02-12
forum: Mythbuntu
---

### Post by w8iss on 2009-02-12
I have upgraded my Ubuntu to Mythbuntu 8.10 about a month ago and every-
thing seemed to be working correctly at the time.

Now I am finding that I have to FORCE mythfilldatabase to every so often
to update the channel schedule.

I found this out after two weeks and was setting up recordings and found
that I didn't have anything listed after a few hours. Last update was 
close to two weeks prior. Now when I start setting up recordings, I close
the backend and then let mythfilldatabase run and I am good for another
two weeks roughly unless there is a special event that happens.

Is there something that I have done differently then when I was running
KnopMyth that I am not aware of or is this something that has been dis-
cussed that I couldn't find in my search of the forum?

Thanks in advance,

James W8ISS

---

### Post by movieman on 2009-02-12
There's an option somewhere in the setup to enable automatic database updates; I forget exactly where.

---

### Post by BigGeoff on 2009-03-04
I have the same problem with 8.10 unfortunately this is my first experience of Mythbuntu or MythTV so I have nothing to compare it with. However, I have the automatic option checked with an update frequency of 1 day anywhere between 00:01 and 23:00 yet it still doesn't update itself so I'm a bit lost too.

Geoff

---

### Post by w8iss on 2009-03-04
I went looking for that checkbox and found it but still have to manually
force a update in a terminal of mythfilldatabase.

I have been having some other issues also, but I will comment on those as a
separate issue in the near future.

James W8ISS

---

### Post by crez79 on 2009-03-04
I was (and apparently still do a little bit) having problems with mythfilldatabase segfaulting ending up with a corrupted database. I am not sure if the corruption was a cause of or result of the segfaulting. Every time mythfilldatabase runs automatically it segfaults. I still have data though somehow. I enabled mythfilldatabase logging in the setup and will see what it says. The corrupt database would snowball into a locked up everything needing a kill of frontends and repair and restart of backend. I moved the primary backend to one of the slaves and is working much better. I am not sure what I "tweaked" to do so much damage, but things are working better now.

There were some weird side effects like on the listing advanced search in mythweb the catagories were getting messed up a litte on a few of the entries (like "tv(how" instead of "tvshow", "seri%s" instead of "series" and a few other variations. After I moved the database over, I manually edited the database to fix these 8 or 9 shows and haven't had a corrupt database or crazy entry in almost a day! I couldn't go more than a couple hours before.

I guess what I am trying to suggest is to check the logs to see if mythfilldatabase is segfaulting and to enable logging to see what's going on. Maybe even clear that check box, exiting and then going back and rechecking it. Sometimes that will make it re-establish the necessary settings to get it to work. I don't know much about the inner workings, but try to learn along the way, and a little trial and error, and error, and error....

---

### Post by theophile on 2009-03-04
Run it as a cron job. That way you don't have to worry about it.

---

### Post by jbman on 2009-03-04
> **theophile said:**
> Run it as a cron job. That way you don't have to worry about it.

agreed

---

### Post by BigGeoff on 2009-03-05
True guys, but I shouldn't have to run a cron job it is supposed to do it on it's own.
I shall enable logging and also uncheck/recheck the automatic box just in case it works.

Geoff

---

