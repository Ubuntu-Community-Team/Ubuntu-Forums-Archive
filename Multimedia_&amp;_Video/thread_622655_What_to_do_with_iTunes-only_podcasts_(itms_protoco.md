---
title: "What to do with iTunes-only podcasts (itms protocol)?"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by tak1150 on 2007-11-25
I'm sure this is a common problem, but I couldn't find a solution for it on this forum.

There is a podcast that I really want to subscribe to, but when I click on the subscription button, a popup window give me this sad message:

> Firefox does not know how to open this address because the protocol (itms) is not associated with any program.

What can i do with this kind of podcast? Try to run iTunes on wine? Thanks for your input.

---

### Post by josh.on.linux on 2008-01-17
I am looking for the very same.  I think your best bet might be to install iTunes using 

a) Wine
b) CrossOver ($40)
c) Virtualized Windows (VirtualBox, Windows).

If I find anything else, I'll let you know.

Josh

---

### Post by josh.on.linux on 2008-01-17
Found a solution:

There's a python script around that "unvails" the "real" location of iTunes podcast links.

Try to google "itunes-url-decoder.py"

Josh

---

### Post by jarreboum on 2008-04-11
You can indeed replace itms:// with http:// to find a xml document where you can find the file you are looking for.

Is there an explanation as why it still doesn't exist an interpreter of that xml file to display it correctly as a web page? I'm not a coder, but that xml code seems pretty clear, without encryption of any sort.

---

### Post by dee_kay on 2008-06-24
> **jarreboum said:**
> You can indeed replace itms:// with http:// to find a xml document where you can find the file you are looking for.

Is there an explanation as why it still doesn't exist an interpreter of that xml file to display it correctly as a web page? I'm not a coder, but that xml code seems pretty clear, without encryption of any sort.

Yup!  Perfect.  I was trying to add an itpc podcast to Rhythmbox.

```
itpc://audio.todayfm.com/podcasting.xml
```

No joy.  I changed itpc to http and it worked.

The simple solutions are always best.

Many thanks,
Dave.

---

