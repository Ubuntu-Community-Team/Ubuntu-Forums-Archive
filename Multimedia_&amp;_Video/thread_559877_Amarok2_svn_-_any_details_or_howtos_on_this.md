---
title: "Amarok2 svn - any details or howtos on this?"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by xanas3712 on 2007-09-25
I can't find any after searching on the amarok forums, ubuntuforums, etc. so I'm guessing there isn't anything currently.

I ran into an issue when I attempted to build amarok svn (it didn't look like an error in compile that I'd expect, I think I just didn't have it all setup correctly).  This was after setting the kde4 environment variables and installing all the development packages it looked like I needed.

As I'm doing some other things at the moment I can't be as specific on the error I got, but in any case if someone could just post the basic instructions I can probably figure out where I went wrong.

Thanks!

(BTW this is using gutsy)

---

### Post by Fatboy Snarky on 2007-09-28
Hi,

sorry I can't help you right now, but sometime during the next three weeks, I'm going to do an upgrade to Gutsy, and give it a try, too...

---

### Post by shirilover on 2007-09-28
This might be what you're looking for.
[http://amarok.kde.org/wiki/2.0_Development_HowTo](http://amarok.kde.org/wiki/2.0_Development_HowTo)

---

### Post by lunarcloud on 2008-04-17
add 
```
##### Amarok Nightly #####[FONT=monospace]
[/FONT]deb [http://ppa.launchpad.net/maarten-fonville/ubuntu](http://ppa.launchpad.net/maarten-fonville/ubuntu) hardy main[FONT=monospace]
[/FONT]deb-src [http://ppa.launchpad.net/maarten-fonville/ubuntu](http://ppa.launchpad.net/maarten-fonville/ubuntu) hardy main

```
to your sources.list file and
```

sudo apt-get install amarok-nightly
```

---

