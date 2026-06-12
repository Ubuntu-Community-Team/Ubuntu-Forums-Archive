---
title: "Sound not working on boot?"
date: 2009-09-06
forum: Multimedia Software
---

### Post by bertles86 on 2009-09-06
Asus EEE 900A
Ubuntu NBR

Volume Control shows:

HDA Intel (Alsa mixer): PCM not muted but volume at 0%

I can manually put this up and I get sound back for VLC/Exaile etc but only for **one session** then when I reboot it goes back to 0% and I can't hear anything.

Now I think this could be a result of me trying to get Skype working on Ubuntu (which is fruitless in case anyone is wondering, really don't bother - Skype and Ubuntu do not work). And I read in the sound guide purging all the pulse/alsa (what's the difference?) and reinstalling can remove gnome as well, so can someone help me get it back to normal?

---

### Post by kerry_s on 2009-09-06
[http://ubuntuforums.org/showthread.php?p=7899972#post7899972](http://ubuntuforums.org/showthread.php?p=7899972#post7899972)

---

### Post by bertles86 on 2009-09-06
that's different, thanks though kerry. My system sound levels are set at 0% not muted.

---

### Post by kerry_s on 2009-09-06
oh, sorry i was tired at that time. i use a little trick to set my volume at 50% when i log in, no matter what i had it at before, that way the start sound don't give a heart attack when i'm still waking up. :lolflag:

anyway, create a "bin" folder in your home. that is for the script.

in that create a file, i just named mine set-volume, put:

```
#!/bin/sh
amixer set Master 50% unmute >/dev/null
```

make sure you right click that file, properties-> permissions & check the box to let it execute/run.

then just add it to your startup, log out & back in see if it works.

(sorry, pics are out of order, couldn't decide what could help)

---

