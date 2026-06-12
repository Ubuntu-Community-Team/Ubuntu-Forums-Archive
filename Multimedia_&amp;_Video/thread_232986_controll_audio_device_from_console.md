---
title: "controll audio device from console?"
date: 2006-08-09
forum: Multimedia &amp; Video
---

### Post by kreso on 2006-08-09
I'd like to issue a command in the terminal like:

audioctl mute
audioctl set-volume 70%
etc. etc..

does such a program exist?

I need it for my program, but all I ever manage to find is mixer guis either in the terminal or X-based;

---

### Post by louis_nichols on 2006-08-09
try this:

```
amixer set Master 15
```

---

### Post by mpvano on 2006-08-09
Exactly!

Better yet, get the mixer completely set up the way you want it to be configured, then use this command

amixer contents > temp.txt

to save ALL the control settings to a file.

then edit that file to make it into a script full of "amixer set xxxx xx" lines that can be run directly by bash. You should remove lines starting with a semicolon - they're comments. If you want to keep them around, you'll need to change them to # characters.

That way ALL the relevant settings for the card will be correct.

hope this helps...

Mario

---

### Post by kreso on 2006-08-10
thanx you guys!

The reason I needed this is to enable my volume keys in XFCE. I made a little program that queried the current Master volume, and then added/substracted a fragment or muted/unmuted as necesarry.

If anyone needs this, I'll be happy to post

---

