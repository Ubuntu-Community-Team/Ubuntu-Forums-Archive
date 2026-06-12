---
title: "Help with mplayer LIRC"
date: 2008-12-22
forum: Mythbuntu
---

### Post by ttabbal on 2008-12-22
I was wondering if someone had the mplayer commands for LIRC to bind a remote button to enable/disable subtitles and cycle through the available languages? I'm just not sure how to set the "config=" line. The rest is easy enough.

---

### Post by august495 on 2008-12-22
Have you looked at this site:
[http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#INTERACTIVE%20CONTROL](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#INTERACTIVE%20CONTROL)

It has the mplayer keyboard commands.

---

### Post by ttabbal on 2008-12-23
> **august495 said:**
> Have you looked at this site:
[http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#INTERACTIVE%20CONTROL](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#INTERACTIVE%20CONTROL)

It has the mplayer keyboard commands.


I have seen it. The issue is that mplayer is an LIRC client. So it knows how to deal with it internally. So you don't use key commands, you use the mplayer commands directly. I'm just not sure what does what and was wondering if someone had already figured out how to handle subs before I spend a lot of time on trial and error. :)

---

### Post by joho500 on 2008-12-23
You can use ```
mplayer -input cmdlist 
```to see all the available commands you can use with lirc.

Cheers,
Joost

---

### Post by apoulos on 2009-01-04
I use:

config = sub_select # j on keyboard

you can also use:

config = sub_visibility # v on keyboard

---

