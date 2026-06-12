---
title: "[SOLVED] Pitivi Wont Load Clips"
date: 2008-02-13
forum: Multimedia Production
---

### Post by stooshbunutu on 2008-02-13
I tried Pitivi and tried importing the clips, worked ok.

But then when I try and drag clips onto the timeline and it just closes itself. What is with this? how can I fix this 

Please help

---

### Post by jan quark on 2008-02-14
try to run your application through the terminal to do this
look up the command for starting your application in the main menu

system > preferences > main menu

there navigate to the launcher of the application and right click on it and select properties
under command you will probaly see something like 

name  -u%

try out by typing only the name into the terminal first
the next time when your application crashes post the error messages which should be displayed now in the terminal

---

### Post by stooshbunutu on 2008-02-17
Good Idea,

Here is what terminal said from start to finnish

> /usr/lib/pitivi/python/pitivi/pitivi.py:158: GtkWarning: gtk_text_layout_get_iter_at_position: assertion `GTK_IS_TEXT_LAYOUT (layout)' failed
  gtk.main()
Segmentation fault (core dumped)

Hope you can help.

---

### Post by stooshbunutu on 2008-02-19
Any Ideas anyone please this is really buggin me not having a decent video editing software

---

### Post by stooshbunutu on 2008-02-26
So I guess the solution is that it doesn't work on all computers

FYI - i use Avidemux instead now

---

