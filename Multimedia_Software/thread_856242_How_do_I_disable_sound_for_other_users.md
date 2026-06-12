---
title: "How do I disable sound for other users?"
date: 2008-07-11
forum: Multimedia Software
---

### Post by ene_dene on 2008-07-11
I can't disable sounds for other users although when creating users I uncheck the field for audio. In /etc/group file I have:
```
...
audio:x:29:pulse,enedene
...
pulse:x:116:enedene
pulse-access:x:117:enedene
pulse-rt:x:118:enedene
...

```
Does anyone know the solution?

---

### Post by ene_dene on 2008-07-11
For some reason that I can't understand it works now, without any change. I did restart comp before and tried it, but it didn't work, and now it does. :)

---

### Post by jdimas on 2008-10-05
I have pulse disabled (so I can use Skype without problems) and I wasn't able to disable sound to the other user in my computer. Isn't there another way to disable sound to the users other than mine (the administrator?)
Thanks!

---

### Post by Keymaster on 2008-10-13
I'm looking to disable sound for certain users as well.  Some users tend to listen to music louder than others.

Edit: I heard that you can create an .asoundrc file in the users home directory ~/ that can set their max volume to zero (or an incredibly low number)  I'm not sure how to do this though.  If you figure it out please, PLEASE PM me.  Thanks

---

