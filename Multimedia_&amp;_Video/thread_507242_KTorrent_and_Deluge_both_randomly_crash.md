---
title: "KTorrent and Deluge both randomly crash"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by modestmelody on 2007-07-22
Both programs will randomly completely close out with no warning or error message.  Anyone have any ideas?

---

### Post by madmetal on 2007-07-23
> **modestmelody said:**
> Both programs will randomly completely close out with no warning or error message.  Anyone have any ideas?

try to open them from terminal so that you can highlight any error messages ;)

---

### Post by modestmelody on 2007-07-23
> **madmetal said:**
> try to open them from terminal so that you can highlight any error messages ;)

Tried that with Ktorrent, but it automatically opens "out of" the terminal (i.e. spits back out a command line without needing the ampersand at the end) and doesn't seem to spit out error messages later on when it just closes.  Maybe I'll try with Deluge in a bit.  Isn't there a way to quickly type in and see what libraries the two programs are using in common?  My guess is it has something to do with some Bittorrent library both are accessing...

---

### Post by ddrichardson on 2007-09-22
Synaptic, under details, will show you what packages install and what dependancies they use, However having just been through that the only similarities are standard c libraries that were you having problems with you would have more applications chucking you out.

The only similarity I can think of off the top of my head is where the downloaded torrents are to be stored - is there a permission problem in the download directory?

---

