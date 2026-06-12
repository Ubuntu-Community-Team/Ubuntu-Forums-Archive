---
title: "Quodlibet and &quot;open with...&quot; option"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by bYOndo on 2007-06-20
Hello everybody! ubuntu 7.04  user here.
How can I make the player Quodlibet to play my music files directly from Nautilus with the famous "open with..." function? If I link the /usr/local/bin file, it opens the player but nothing happens.
Another similar request; I use Firefox with "mediaplayer connectivity" plugin, it's very powerful but the same here, I don't know how to make Quodlibet interact with it.
Thanks in advance!

bye,
Massimo

---

### Post by tgoose on 2007-06-20
Unfortunately, I don't think Quod Libet's syntax allows this.

The command line to do this is
```
quodlibet --play-file=/path/to/file.ogg
```

This works fine and plays the file before continuning with whatever playlist or browser was being used before.

However, because there's no space before the path, Nautilus won't treat it correctly. I don't know of any easy solution to that, without changing Quod Libet or adding a lot to Nautilus.

---

### Post by bYOndo on 2007-06-21
thanks for reply,
I believe that without a similar standard option, quodlibet cannot become a popular program and it's a shame, because it's a very good player. Think I'll drop a line to the author :)

bye,
Massimo

---

