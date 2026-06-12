---
title: "Listen player doesn't load"
date: 2008-06-20
forum: Multimedia Software
---

### Post by Nightglade on 2008-06-20
Hi there, new to linux here. I've been using "Listen" music player, and I much prefer it over Rythmbox or the default Totem. However, it's no longer working.

When I use the launcher, it appears on the taskbar as "Starting Listen Music Player" and after a few seconds just disappears and doesn't load. I've tried completely removing it and reinstalling it, restarted computer, tried it on a seperate user account and no different..

When I try it from terminal, this is what I get:

nightglade@osiris-desktop:~$ listen
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
nightglade@osiris-desktop:~$ 


I'd really appreciate help on this, thankyou!

---

