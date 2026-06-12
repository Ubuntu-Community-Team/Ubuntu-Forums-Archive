---
title: "Strange Amarok Behavior"
date: 2008-04-28
forum: Multimedia Software
---

### Post by james_xxx on 2008-04-28
Using the Medibuntu Amarok package in Hardy, Amarok "updates the collection" over and over and over. Additionally, every track in my collection is now listed twice.

I do not know whether the official Ubuntu package does the same thing or not.

Is anyone else experiencing this? Any solutions?

---

### Post by james_xxx on 2008-04-29
bump

---

### Post by Zorael on 2008-04-29
I set it up to not update my collection automatically, then I just do manual rescans whenever I've added something new. Not a fix, but a way of dealing with it. :>

---

### Post by james_xxx on 2008-04-29
OK, I think I have it fixed at this point. All I did was delete the files in /.kde/share/apps/amarok that had to do with the database. After that, I restarted Amarok, it scan the collection again, and its behavior is now back to normal.

BTW, thanks for replying to my post!

-J

---

### Post by OnlyWhisky on 2008-05-01
I confirm that bug. Will try your solution but it is still a [BUG]! Developers, please fix it!

---

### Post by diwakergupta on 2008-05-02
I can confirm this bug. I don't want to try your solution yet since then I'll lose all my scores and ratings :(
Any other workaround?

---

