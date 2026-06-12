---
title: "Playing an ISO of a DVD"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by elreteipos on 2007-03-25
I want to play an ISO of a DVD. How can I play it? Should I just mount the ISO and try to open one of the .vob/.ifo files?

---

### Post by aidanr on 2007-03-25
no need to mount it, you can open it with totem or mplayer

edit:// sorry, just noticed you're running kubuntu, so that should read kaffeine or mplayer :)

---

### Post by PilotJLR on 2007-03-25
Totem and Kaffeine can both open the file itself... just open the .iso file with one of them.

---

### Post by elreteipos on 2007-03-25
mplayer: I had to kill it because the window stopped responding after opening the file.
Totem: it doesn't show the DVD menu, so I couldn't access what I wanted to see.
Kaffeine: says it doesn't have a plugin to open the file.

[img]http://img256.imageshack.us/img256/7726/kaffeineerrornr6.jpg[/img]

---

### Post by chewearn on 2007-03-25
How to mount iso:
[http://ubuntuforums.org/showthread.php?t=386281](http://ubuntuforums.org/showthread.php?t=386281)

Try VLC to open the mounted directory, using File > Open Directory

---

### Post by rumli on 2007-04-27
After installing totem-xine and libdvdcss2, run:

```

totem dvd://full/path/to/dvd.iso

```

---

### Post by ubu-for on 2007-04-27
> **aidanr said:**
> no need to mount it, you can open it with totem or mplayer

No, you don't!

Just install VLC, right click on ISO and choose "Open with>>VLC" or "Open with>>Other programs" and enter:

```
vlc
```

---

