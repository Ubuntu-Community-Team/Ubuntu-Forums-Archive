---
title: "Rhythmbox doesn't open"
date: 2016-03-20
forum: Multimedia Software
---

### Post by lynyrdskynyrd385 on 2016-03-20
I've had the same issue on two fresh installs of Ubuntu 14.04 and now out of curiosity I tried 15.10 and had the same issue but 15.10 had a bit different output when I tried opening it in terminal. This has also been after I completed the initial slew of updates. I've researched it a bit and cant find anyone with exactly the same issue. I've tried to purge and uninstall/reinstall and same issue. Not sure if its hardware related? I've only ran Ubuntu on laptops before but wanted to try gaming so installed it on my desktop.

Here's output I get when trying to open from terminal.

```
user@desktop:~$ rhythmbox

(rhythmbox:3138): libsoup-CRITICAL **: soup_server_quit: assertion 'priv->listeners != NULL' failed

(rhythmbox:3138): GLib-GObject-CRITICAL **: object SoupServer 0x2bc0dc0 finalized while still in-construction

(rhythmbox:3138): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid). Please use GInitable instead.

(rhythmbox:3138): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist


(rhythmbox:3138): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist


(rhythmbox:3138): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist


(rhythmbox:3138): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist


(rhythmbox:3138): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist


(rhythmbox:3138): Gtk-WARNING **: Duplicate child name in GtkStack: Add to Playlist

^C
```

---

