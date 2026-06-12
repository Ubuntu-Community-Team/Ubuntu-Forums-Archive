---
title: "XMMS status in CLI ?"
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by LinuX-M@n1@k on 2008-04-03
I was wondering if there's a way to see what song is playing XMMS in CLI ( Command Line Interface, for those who don't know what CLI means :) ) Something like "<Artist> - <Ttile>.<Format>"
Cheers

---

### Post by LinuX-M@n1@k on 2008-04-03
.

---

### Post by gsmanners on 2008-04-03
I don't know if this works with Xmms, but with Audacious (which is based on  Xmms), you can do something like this:

lsof | grep music

Where "music" is part of the name of the folder where the songs are.

---

### Post by LinuX-M@n1@k on 2008-04-04
not working. other ?

---

