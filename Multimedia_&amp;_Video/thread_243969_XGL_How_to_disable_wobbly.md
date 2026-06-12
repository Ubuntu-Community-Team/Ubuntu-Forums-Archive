---
title: "XGL: How to disable wobbly?"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by evillawngnome on 2006-08-25
I finaly got xgl working after following some howtos. I love the performance boost, but i cant stand the wobbly plugin. How do i diable it?

---

### Post by Nordkraft on 2006-08-25
You open gconf-editor:
```
$gconf-editor
```
browse to apps>compiz>general>allscreens>options. Here you find the key "active_plugins" and edit it, ie. remove "wobbly":)

---

### Post by evillawngnome on 2006-08-25
Perfect! Thanks.

---

### Post by TwoWordz on 2006-09-04
I have don't have it in my plugin list and I am still having the wobbly efect. I is making me sick...

Am I missing something? It seems whatever I change in gconf-editor, nothing is changing in compiz settings.

TW

---

