---
title: "can't escape from delete screen under certain circumstances"
date: 2008-03-28
forum: Mythbuntu
---

### Post by Scott Atkinson on 2008-03-28
Well, having learned (again) that I'm a moron, and that my Myth installs were crashing and burning because nothing was expiring, I've hit a small secondary issue.

I can delete recordings from the 'delete recordings' screen - using my keyboard - but after I delete the last one, I can't hit escape and get back to the rest of MythTV.

Is this a known bad thing, or my stupidity again?

Scott A.

---

### Post by foxbuntu on 2008-03-28
Not sure if this is a known condition, but one way to check what is going on:

Close the frontend, start it in terminal/xterm:
```
mythfrontend -v
```

This will run the frontend with verbose debugging, go try to reproduce this situation and once it have it hit:
```
alt+tab
```
to see the erminal again, then I would suggest if it is not something you can figure out directly copy it up to the forums and we can take a look of it.

---

### Post by Scott Atkinson on 2008-03-28
Thanks. Will do.

s.

---

