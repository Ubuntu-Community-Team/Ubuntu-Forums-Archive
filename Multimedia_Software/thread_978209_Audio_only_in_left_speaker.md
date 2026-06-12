---
title: "Audio only in left speaker"
date: 2008-11-10
forum: Multimedia Software
---

### Post by dgavenda on 2008-11-10
Here's the weirdness:

1) xfce and kde no sound but amarok and audacious show it's playing

2) gnome - used to have sound in both speakers.  Now only the left.  

3) Both speakers still work. 

Sound card is:
03:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
03:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
 

Ideas how to troubleshoot this?

---

### Post by dgavenda on 2008-11-11
Gonna try this: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

---

### Post by dgavenda on 2008-11-11
Ok that didn't work.


Anyone have any ideas?  It worked at one time w/ 8.10 and the only thing to chg was the usual updates.

---

### Post by psyke83 on 2008-11-11
Try checking your PCM volume:

```
$ alsamixer -Dhw
```

---

### Post by dgavenda on 2008-11-11
Ya that's one of the first things I looked at.

I have sound in one speaker (left) but not the right.  Speakers are fine.  Doesn't work in xfce nor kde.  Just gnome has sound in one speaker.

Such a pain......

---

### Post by dgavenda on 2008-11-11
Ok..I figured out the right speaker not working.  Wire was not firmly in all the way but only affected the right speaker.

Regardless, sound only works in gnome.  It doesn't work in kde or xfce.  What does gnome do for sound that xfce/kde don't?

---

### Post by _tarzan_ on 2008-11-13
hi all i m a new user and do not have lot of technical knowledge
neways only one of my speakers is working in ubuntu 8.04 while it works fine with windows xp
I have dell latitude D520 and Creative 2.1 speakers
plz help

---

### Post by Fir3chi3f on 2008-11-13
try double clicking the speaker in the upper right hand corner and making sure that the two bars in the same columns all line up

---

