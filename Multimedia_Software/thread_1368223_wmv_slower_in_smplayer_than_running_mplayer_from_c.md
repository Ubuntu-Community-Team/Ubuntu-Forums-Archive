---
title: "wmv slower in smplayer than running mplayer from commandline?"
date: 2009-12-30
forum: Multimedia Software
---

### Post by BagRackRider on 2009-12-30
Like the title says.
When I try to play wmv files in smplayer they play MUCH slower than running just mplayer from the commandline, why? Afaik I use the same options in both smplayer and mplayer.

Is there a way I can make sure the same options are passed, so I can find out what's causing it?

---

### Post by rvm4000 on 2009-12-30
You can see what options are passed to mplayer in Options->View logs->mplayer.

---

### Post by BagRackRider on 2009-12-30
SMPlayer sure did add a lot of extra stuff.
When starting mplayer manually with the same commandline that SMPlayer passes I don't get any picture?

---

### Post by rvm4000 on 2009-12-31
Don't use in command line the -wid option.

---

### Post by BagRackRider on 2010-01-01
Thanks!

It was the -framedrop option that caused the wmv to play "slower", so it wasn't SMPlayers fault! ;)

Keep up the good work with SMPlayer!

---

