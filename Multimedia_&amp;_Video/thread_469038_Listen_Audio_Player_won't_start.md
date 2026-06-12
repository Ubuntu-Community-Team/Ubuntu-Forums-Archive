---
title: "Listen Audio Player won't start"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by nightbeing86 on 2007-06-09
Hello folks.

While trying to get a decent Amarok replacement for my gnome-desktop (feisty), i want to give Listen a try.
I somehow don't like Exaile too much, and Banshee really choked on my not-too-small music collection.

So I installed listen via apt, but it didn't start. I tried to run it in a terminal window, and all it gave me was this:

```
nightbeing86@n8-desktop:~$ listen
/usr/lib/listen/stock.py:135: GtkWarning: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
  try:icons.add(SHUFFLE,  gtk.IconSet(gtk.icon_theme_get_default().load_icon("stock_shuffle",-1,gtk.ICON_LOOKUP_USE_BUILTIN)))
/usr/lib/listen/stock.py:135: Warning: g_object_ref: assertion `G_IS_OBJECT (object)' failed
  try:icons.add(SHUFFLE,  gtk.IconSet(gtk.icon_theme_get_default().load_icon("stock_shuffle",-1,gtk.ICON_LOOKUP_USE_BUILTIN)))
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 219, in <module>
    ListenApp()
  File "/usr/lib/listen/listen.py", line 120, in __init__
    stock.stock_init()
  File "/usr/lib/listen/stock.py", line 135, in stock_init
    try:icons.add(SHUFFLE,  gtk.IconSet(gtk.icon_theme_get_default().load_icon("stock_shuffle",-1,gtk.ICON_LOOKUP_USE_BUILTIN)))
TypeError: pixbuf should be a GdkPixbuf

```

Ain't got any 3rd-party repositories active, so this is the "ubuntu-listen-version".

Any ideas how to fix this? I'd really like to try this player, since the features it offers seem to be the closest to amarok you can get without loading a whole bunch of kde-libs ;)

thanks in advance
paul

---

### Post by moeFinley on 2007-06-09
It seems to be having trouble with your version of GTK?  Have you tried a complete reinstall?

---

### Post by nightbeing86 on 2007-06-10
reinstall of listen, gtk or ubuntu?

the last two are relatively fresh, just set up this box last week and did not install any third party packages but pidgin.

---

### Post by moeFinley on 2007-06-10
I ment reinstall Listen.  You can also delete the hidden .listen folder from your home folder to remove everything.

Not sure if it will make a difference but it's worth a try.

---

### Post by nightbeing86 on 2007-06-10
well, did that quite a few times over then ;) including apt-get autoremove for all the dependencies it installed.
didn't delete the .listen folder though, but it's empty anyway. since it never started, so it never made any config files there.

---

### Post by boheleven on 2008-02-09
Dragging up and old post, but i was having the same problem and managed to get Listen loaded by editing stock.py

```
sudo gedit /usr/lib/listen/stock.py
```

and removing these two lines;

```
Try: icons.add (SHUFFLE, gtk.IconSet (gtk.icon_theme_get_default (). Load_icon ( "stock_shuffle", -1, gtk.ICON_LOOKUP_USE_BUILTIN))) 
except gobject.GError:pass Except gobject.GError: pass

```

and Listen should work fine.

---

### Post by newone757 on 2008-03-14
^^

thankyou, i had this problem and editing those lines worked PERFECTLY

---

### Post by j800r on 2008-06-12
i had the problem too. enquired in irc chat, and i was directed to this thread, and it solved the problem instantly. Thanks a lot. ^^

---

### Post by EnigMattic on 2008-07-11
> **boheleven said:**
> Dragging up and old post, but i was having the same problem and managed to get Listen loaded by editing stock.py

```
sudo gedit /usr/lib/listen/stock.py
```

and removing these two lines;

```
Try: icons.add (SHUFFLE, gtk.IconSet (gtk.icon_theme_get_default (). Load_icon ( "stock_shuffle", -1, gtk.ICON_LOOKUP_USE_BUILTIN))) 
except gobject.GError:pass Except gobject.GError: pass

```

and Listen should work fine.

Yep! Thanks! Worked for me!!!

---

