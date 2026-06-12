---
title: "Rhythmbox: &quot;Unable to activate plugin Portable Players - iPod&quot;"
date: 2010-04-13
forum: Multimedia Software
---

### Post by jon.reeve on 2010-04-13
I keep getting this error every time I try to enable the ipod plugin for rhythmbox. Is there something I can do to repair this?

---

### Post by jon.reeve on 2010-05-21
Ok, I ran rhythmbox from a terminal and I get this error: 

```
(rhythmbox:11745): Rhythmbox-WARNING **: libiphone.so.0: cannot open shared object file: No such file or directory

(rhythmbox:11745): Rhythmbox-WARNING **: Could not load plugin ipod

(rhythmbox:11745): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Portable Players - iPod'


```

I also tried installing ifuse as suggested on some of the posts about libiphone. Most of the stuff written out there is about Karmic, so I'm having difficulty figuring this out. 

I'm on Lucid 64, BTW. 

Any ideas?

---

### Post by jon.reeve on 2010-06-01
I've also tried purging rhythmbox and deleting the ~/.local/share/rhythmbox directory, to no avail. Any ideas? I might try a fresh install of Ubuntu

---

