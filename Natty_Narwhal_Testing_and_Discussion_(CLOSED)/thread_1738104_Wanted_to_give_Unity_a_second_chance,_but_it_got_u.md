---
title: "Wanted to give Unity a second chance, but it got up and left!!"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Atamisk on 2011-04-24
Good morning all

I've been using the beta of Natty since it came out, and i must say, i'm very excited about the new release. At first, i was rather annoyed by unity, and just switched to ubuntu classic, and I've been running like that ever since. Well, after other people started to comment about how Compiz now works in Unity, I'm again intrigued. Unfortunately, i went back over to the Unity session, and Unity never starts. I just get my background and one icon (CD in the drive). 

Any ideas?
-Aaron

---

### Post by wojox on 2011-04-24
Did you activate the video driver?

---

### Post by r-senior on 2011-04-24
Did you change Compiz settings while you were in Classic?

Running ```
unity --reset
``` might do the trick, but bear in mind that might trample on any custom settings you made for Compiz.

---

### Post by Atamisk on 2011-04-24
If i back up gconf, i should be able to replace them, correct?

---

### Post by mc4man on 2011-04-24
While some people have posted otherwise, in a _good, current install _the compiz setting (what's enabled, disabled, key binding to some degree) are separate in the unity and classic logins
They are maintained in separate profiles and do not affect the other

---

