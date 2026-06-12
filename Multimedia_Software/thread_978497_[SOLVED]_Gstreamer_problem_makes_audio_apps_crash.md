---
title: "[SOLVED] Gstreamer problem makes audio apps crash"
date: 2008-11-11
forum: Multimedia Software
---

### Post by cyber_bushi on 2008-11-11
Hey there,

my rhythmbox and banshee crash all the time when I try to play music.
A rhythmbox -d on the console tells me the following:
```
(12:02:46) [0x86f3408] [rb_shell_player_error] rb-shell-player.c:3421: playback error while playing: Internal GStreamer error: state change failed.  Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer.
```
Did anyone else encounter this problem or know any solution to this?
Already tried to reinstall all gstreamer related packages...
Any ideas?
Thanks!

P.S. Intrepid / Ubuntu

**UPDATE:** same thing with banshee - amarok works (probably using different libs)

---

### Post by cyber_bushi on 2008-11-13
If you change your audiosink, you might want to set it back to the original value once you don't use your bluetooth headset anymore.
Thanks to the Gnome guys!
[http://bugzilla.gnome.org/show_bug.cgi?id=560502](http://bugzilla.gnome.org/show_bug.cgi?id=560502)

---

