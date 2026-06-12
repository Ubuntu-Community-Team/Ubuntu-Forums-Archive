---
title: "I can't get s-video out to work"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by trommas on 2007-02-07
I've searched everywhere I can think of, and tried several apps. Yet, I can't get s-video to work on my laptop. Even tried editing my xorg (This worked, but left me with a blank desktop screen).

What do I need to do after plugging in my s-video cable that will make Ubuntu understand that it's time to display video on my connected TV?


I'm running Feisty with binary drivers installed.

---

### Post by renzokuken on 2007-02-07
[http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia+tv+out](http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia+tv+out)

this worked for me using an nVidia card

---

### Post by trommas on 2007-02-07
> **renzokuken said:**
> [http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia+tv+out](http://www.ubuntuforums.org/showthread.php?t=98456&highlight=nvidia+tv+out)

this worked for me using an nVidia card

This worked. Thanks!

This guide is 2 years old, maybee there is a better way to do it?

It would be great if the "set screen resolution" in the control panel was switched out for "display settings" -more like winxp- to handle all these kind of things.

---

### Post by renzokuken on 2007-02-08
glad it worked for you. i always do it this way on reinstalling, i dont know if there is anything newer. it may even be that that the nvidia xorg.conf configurator (sudo nvidia-xconfig) does it for you now, i've never tried though.

---

