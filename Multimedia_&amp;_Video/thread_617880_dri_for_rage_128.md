---
title: "dri for rage 128"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by Phantom784 on 2007-11-19
I installed Xubuntu on an old computer that has an ati rage 128 graphics card.  However, I can't seam to get direct rendering to work.  I remember having it working a while ago, I think on kubuntu dapper.  I'm having no such luck now.  I changed the driver from "ati" to "r128" in xorg.conf, and tried reducting the colour depth from 24 to 16, both with no effect.  Any ideas?

---

### Post by NT4usB on 2007-11-19
I had it once too but haven't found it since. iirc, indication it was working was a black cursor or something...
Gonna have to hook that box back up and play some more.

---

### Post by NT4usB on 2007-11-20
found this in my bookmarks.
[http://ubuntuforums.org/showthread.php?t=76154&page=2](http://ubuntuforums.org/showthread.php?t=76154&page=2)

---

### Post by Phantom784 on 2007-11-20
I tried compling the drivers as reccommened in that link, but it wouldn't work, probably because it was for breezy.  I did manage to get some fps improvement in glxgears by installing libgl1-mesa-dri, but it still didn't give me direct renedering and and the gears were still choppy (well, for some reason, they were smooth for about a second, but then got choppy).

---

### Post by NT4usB on 2007-11-20
Well, I had it working in Edgy on a old pos PIII 550. I remember because the cursor changed colors or something (I think as a result of using Xv.) iirc, the display was flaky like the cursor icon hung up or something but anyway, it got good gears and dri so I know it works.
I hooked up the wrong box last night and got off on a tangent. Lets see if we can grab the right one tonight and figure it out all over again...

---

### Post by Phantom784 on 2007-11-20
edgy isn't to far from gutsy, so maybe it'll work.  try and find out what you did, because i'm at a loss at this point.

---

### Post by Phantom784 on 2007-11-21
I figured it out :)  First of all, make sure the package libgl1-mesa-dri is installed.  Then enter "sudo cp /usr/lib/dri/r128_dri.so /usr/X11R6/lib/modules/dri/"  Hope this works, I forget everything I did when fooling around to make it work, and something else I did might have also been necessary.

---

