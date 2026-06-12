---
title: "How to view pictures by modification date ?"
date: 2011-03-25
forum: Multimedia Software
---

### Post by mrpenguin on 2011-03-25
When I go in a file with pictures and right click on it I tell it to arrange pictures by modification date but when I start viewing the pictures and click on next then it shows them to me in Alphabetical order.

I am using Eye of GNOME 2.32.0 to view pictures

How do I get this application to show me the pictures by modification date ?
I cant find any setting for this

---

### Post by nothingspecial on 2011-03-26
Don't know how to do this with eye of gnome but if all the pictures are in the same directory

```
feh -F -f $(ls -t)
```

should work.

The capital F is optional, that means full screen. The little f flag means specify a file list to which you pass ls -t which is list by modification time.

Should work in theory.

Press the space bar to see the next picture. Press Q to exit.
[I]

***edit*** of course you have to install feh first ***edit***[/I]

---

### Post by SeijiSensei on 2011-03-26
**Gwenview** supports directory sorts by name/date/size.  (I can't seem to make it reverse the sort order, though.)  Gwenview became the default KDE image viewer a while back.  From looking at its dependencies it doesn't seem like installing it into a GNOME desktop would bring along very much KDE "baggage," though.

---

### Post by mrpenguin on 2011-03-26
Thanks ... I installed Gwenview

I dont understand why linux picture viewers has such a big problem with viewing pictures in any other way but alphabetical order

---

### Post by shantiq on 2011-05-04
> **nothingspecial said:**
> Don't know how to do this with eye of gnome but if all the pictures are in the same directory

```
feh -F -f $(ls -t)
```

should work.

The capital F is optional, that means full screen. The little f flag means specify a file list to which you pass ls -t which is list by modification time.

Should work in theory.

Press the space bar to see the next picture. Press Q to exit.
[I]

***edit*** of course you have to install feh first ***edit***[/I]


thanx   very handy

---

