---
title: "No sound from Line In - Using Karmic"
date: 2010-03-30
forum: Multimedia Software
---

### Post by 666porcondissaum on 2010-03-30
Hi... something happened after the last or one of the last updates here. I used to tune my guitar and also play through creox with some effects but suddenly the line in isn't working anymore. And every time I open the sound preferences and work around with the input sources, at each source only front mic works. Any idea?

Also, the gnome-alsamixer is screwed(talking about capture devices)... nothing seems to work well out there.
:guitar:](*,)

---

### Post by lidex on 2010-03-31
In a terminal enter:
```
alsamixer
```
Press F4 for capture devices. Scroll over to entries with no "meter" showing, only text, using left-right arrow keys. Use up-down arrow keys to toggle between mic and line.

---

