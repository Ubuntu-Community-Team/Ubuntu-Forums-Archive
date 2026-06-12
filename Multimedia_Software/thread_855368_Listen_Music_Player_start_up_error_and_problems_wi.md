---
title: "Listen Music Player start up error and problems with IDL"
date: 2008-07-10
forum: Multimedia Software
---

### Post by baddison on 2008-07-10
My first problem is with Listen Music Player.  After installing some packages to get IDL to work Listen stopped working.  In fact Listen won't even start up.  Here is the error message when I run in terminal:
brett@brett-laptop:~$ listen
/usr/lib/listen/stock.py:135: GtkWarning: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
  try:icons.add(SHUFFLE,  gtk.IconSet(gtk.icon_theme_get_default().load_icon("stock_shuffle",-1,gtk.ICON_LOOKUP_USE_BUILTIN)))
/usr/lib/listen/stock.py:135: Warning: g_object_ref: assertion `G_IS_OBJECT (object)' failed
  try:icons.add(SHUFFLE,  gtk.IconSet(gtk.icon_theme_get_default().load_icon("stock_shuffle",-1,gtk.ICON_LOOKUP_USE_BUILTIN)))
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 218, in <module>
    ListenApp()
  File "/usr/lib/listen/listen.py", line 119, in __init__
    stock.stock_init()
  File "/usr/lib/listen/stock.py", line 135, in stock_init
    try:icons.add(SHUFFLE,  gtk.IconSet(gtk.icon_theme_get_default().load_icon("stock_shuffle",-1,gtk.ICON_LOOKUP_USE_BUILTIN)))
TypeError: pixbuf should be a GdkPixbuf

My second problem is with a program called IDL.  After installing the packages I was told to install I still get the following error message when I run IDL: Fatel error initializing DML
Any help would be appreciated.  Thank you
See picture below:
[IMG]http://img89.imageshack.us/img89/273/idlerrorqr0.jpg[/IMG]

---

### Post by xc3RnbFO8P on 2008-07-10
Listen:
> boheleven
February 9th, 2008, 04:11 PM
Dragging up and old post, but i was having the same problem and managed to get Listen loaded by editing stock.py

sudo gedit /usr/lib/listen/stock.py

and removing these two lines;

Try: icons.add (SHUFFLE, gtk.IconSet (gtk.icon_theme_get_default (). Load_icon ( "stock_shuffle", -1, gtk.ICON_LOOKUP_USE_BUILTIN)))
except gobject.GError:pass Except gobject.GError: pass


and Listen should work fine.

---

### Post by baddison on 2008-07-16
Works thanks

---

### Post by prodriguezmad on 2008-11-08
Hello,

What is the output or the result when you execute 'idldemo' from the command line?

Maybe you need to install older versions of the standard C++ library (from Synaptic search for libstdc++ and choose the one with the 5).

---

