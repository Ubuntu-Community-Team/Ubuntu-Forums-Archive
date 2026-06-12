---
title: "menu entries not available in cheese, blank video window"
date: 2012-02-04
forum: Multimedia Software
---

### Post by cometdog on 2012-02-04
Trying to get my webcam working in 11.10, so I installed Cheese.  When I open it, the video window is blank and nearly all of the menu entries are greyed out.

My webcam (Microsoft Lifecam Cinema) works just fine with guvcview, and used to work with Cheese on Ubuntu 10.04.

If I start cheese from the terminal, I see messages like this:

```
(cheese:3799): Gtk-WARNING **: Attempting to add a widget with type GtkImage to a GtkButton, but as a GtkBin subclass a GtkButton can only contain one widget at a time; it already contains a widget of type GtkLabel
```

and finally

```
** (cheese:3799): WARNING **: Could not negotiate format
```

Does anyone have any suggestions for troubleshooting?  I wonder if the trouble I'm having with Cheese is the same which causes some online applications not to recognize that I have a webcam.

---

### Post by billcauley on 2012-02-04
Ditto!

---

### Post by cometdog on 2012-02-11
I reported this as bug #930671.
[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930671](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/930671)

---

