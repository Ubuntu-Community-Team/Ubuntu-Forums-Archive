---
title: "Nautilus freezes in folders with audio files!"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by saz on 2007-10-31
Can you believe this???

Every time I open a folder that contains audio files in it, nautilus completely freezes... i have to force quit and when it quits it opens automatically another nautilus window on my local folder (/home/user)...

i use ubuntu for a long time and that never occurred to me... it all began since i upgraded to Gutsy (clean install)...

---

### Post by saz on 2007-11-03
anyone pls help me? it's getting really annoying...

---

### Post by snsoneee on 2007-11-03
same here.
im runing a 64 Intel pendium d and i have 1gig RAM

---

### Post by Tomàs M. on 2007-11-04
Perhaps changing some view options can help you: [http://ubuntuforums.org/showthread.php?t=470947](http://ubuntuforums.org/showthread.php?t=470947)

---

### Post by saz on 2007-11-04
didn't work.. had to reinstall... thanks anyway, at least you answered... ;)

---

### Post by crash0 on 2007-11-23
same problem here... 64-bit gutsy

---

### Post by AndrewHuk on 2007-11-24
I have the same problem, but when I changed the view to "List View" it works fine, but as soon as I put it back in icon view it freezes.


Andrew

---

### Post by AndrewHuk on 2007-11-25
Hello All,

Further to my post last night, I have found if you do the following Nautilus file manager does not freeze when you have audio files in it.

Open Terminal and run

```
gconf-editor
```

Then browse to Apps > Nautilus > Preferences

Look for Preview_sound and change from local_only to never

Thats it.

Basically from what I see is that it freezes with this because it tries to play a preview of the sound when you put/ the move the mouse over the icon.

Hope this helps.

Andrew

---

### Post by Buzzdee on 2007-12-24
works perfectly fine, thanks.
by the way, this is a very weird feature/bug (?) - i recommend to disable this by default.

---

### Post by saz on 2008-03-27
i'm sorry you discovered that only after i did a fresh install xD thanks anyway!

---

