---
title: "Exaile: need to reload library each time I started it"
date: 2010-03-23
forum: Multimedia Software
---

### Post by otriades on 2010-03-23
Hello,

I have xubuntu 9.04 and exaile 0.3.1. Every time I start exaile I have my collection empty and I need to reload it. I close de program normally with file -> quit.
I started de program from command line and I don't get any error messages.
I tried removing exaile (sudo apt-get remove exaile), then deleting dir /home/me/.exaile and then reinstalling it and I have the same problem.
Can anybody help me? Thanks in advance...

---

### Post by otriades on 2010-03-24
I found a solution: reset the collection with:

```
rm ~/.local/share/exaile/music.db
```

See this:

[http://www.exaile.org/forum/viewtopic.php?f=4&t=957](http://www.exaile.org/forum/viewtopic.php?f=4&t=957)

---

