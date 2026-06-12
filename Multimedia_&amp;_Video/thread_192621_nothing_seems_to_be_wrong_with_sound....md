---
title: "nothing seems to be wrong with sound..."
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by homicidalmo0se on 2006-06-08
but it still doesn't work. ](*,) 

i did lspci. and it came up with this: [http://pastebin.com/768989](http://pastebin.com/768989)

so it detects it. i also went into system > preferences > sound and it said hda intel at the bottom. which confirms that it's there.

when i do alsamixer, it has the sliding bars and everything.

so i don't know what's wrong. anyone know?

---

### Post by 3saul on 2006-06-09
I'm having the same problem...when will we get some help on the sound issue Ubuntu? FC5 works so well in comparison...hmmmm....

---

### Post by capi on 2006-06-09
Have you tried adding yourself to the audio group?

```
sudo adduser <<name>> audio
```

[http://www.ubuntuforums.org/showthread.php?t=188872](http://www.ubuntuforums.org/showthread.php?t=188872)

---

### Post by 3saul on 2006-06-09
Tried that. For me it actually loads the driver...but gnome can't see it nor any of the other mixers (echomixer).

I have an onboard intel soundcard that I disable. Just to test it out I enabled it and all works fine....but I have to (and want to) use my darla card!

---

