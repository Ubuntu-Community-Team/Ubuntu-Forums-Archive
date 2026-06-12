---
title: "Amarok ipod sync"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by ohzopants on 2007-02-28
I had previously spent hours trying to get various programs to play nice with my ipod under ubuntu on my old computer.  Since I bought a new computer, amarok works flawlessly with my ipod (as a former ml_ipod/winamp user, the bar for performance had been set pretty high; and I am still impressed by the amarok/ipod interaction).

One thing is still bothering me however, there doesn't seem to be an easy way to sync my amarok collection with my ipod.  I just want a button that will check for new files in my collection and add them to the transfer queue, but I can't find one.  I am left with the (acceptable) method of keeping track of new stuff and transferring it manually.

I am totally blind, or is this feature truly missing from amarok?

---

### Post by linuxnoob123 on 2007-02-28
i use gtkpod, its really easy to use. it even supports transfer of videos.

---

### Post by TimJBart on 2007-03-01
I have this exact same issue with amarok.  Just give me a sync button and  I'd be happy, it has everything else!  Keeping track of stuff manually is such a pain when you don't have much time, you just wanna connect up your ipod, let it do its thing and then eject it.  Job done.

In another thread I was also recommended **gtkpod** so I'm going to give that a shot tonight.

How often does Amarok get updated, and how likely is it that they will add a SYNC button?

---

### Post by hanexar on 2007-03-02
I haven't tried it, but if you got to playlist -> smart playlist -> all collection and right click on it, you should have the "sync to media device" option.

It should do the tricks... Just haven't tried it.

---

### Post by ohzopants on 2007-03-02
Thanks hanexar.  I will definitely try that next time I need to add something.
As for gtkpod, I tried it and I found it to be terrible.

---

### Post by hanexar on 2007-03-02
I just tried it with a standard playlist (can't try it with the full collection it doesn't get on a 4Gig ipod) and it works perfect, you just have to click back on media device and hit the transfer button.

So it's basically 2 clicks: one on sync, one on transfer..  Still easier than tracking stuff.

---

### Post by ohzopants on 2007-03-04
Well I just tried this method and it does work for adding all the new files automatically.  But, it does delete (from the ipod) files that were removed from the library. :(

Guess I'll just have to cope with that...

Thanks again hanexar

---

### Post by esaym on 2007-03-04
[QUOTE=TimJBart]

How often does Amarok get updated, and how likely is it that they will add a SYNC button?[/QUOTE]

I actually don't think it will ever be updated.  Kinda makes me mad.  Dapper seems to be stuck with version 1.4.3, edgy has 1.4.4 and feisty has 1.4.5.  There doesn't appear to be any work with the devs as far as updating versions that are already installed.  1.4.5 does have some kind of new feature:
```
Synchronize play count, last played time and date of modification to iPods. Patch by Michael. (BR 136759)
```

[http://amarok.kde.org/en/node/201](http://amarok.kde.org/en/node/201)

Not sure what that means though.  Right now I am trying to figure out what it will take to bring dapper up to the latest version of gtkpod. It looks simpler and the version of amarok on dapper has a bug in to where what would normally be a 10 minute transfer in windows takes 1 hour on ubuntu :(

---

