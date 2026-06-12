---
title: "Listen audio player can't play anything"
date: 2010-03-06
forum: Multimedia Software
---

### Post by evanct on 2010-03-06
This is a fresh install of Listen from synaptic on 9.10. I can launch it with no obvious problems:

```
evan@evan-laptop:~$ listen
AttributeError: 'module' object has no attribute 'Element'
/usr/lib/pymodules/python2.6/musicbrainz2/model.py:21: DeprecationWarning: the sets module is deprecated
  from sets import Set
listen:107: Warning: g_set_prgname() called multiple times
  gnome.libgnome_module_info_get(), sys.argv, []
/usr/lib/listen/widget/misc.py:33: DeprecationWarning: Use the new widget gtk.Tooltip
  TIP = gtk.Tooltips()
/usr/lib/listen/widget/preference.py:24: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
/usr/lib/listen/widget/misc.py:35: DeprecationWarning: Use the new widget gtk.Tooltip
  TIP.set_tip(widget,text,None)
Tray icon attached

```

When I try to play anything it appears as "Now Playing" but it stays at 00:00, with the output:

```
ERROR    listen.player.fadebin.PlayerBin   0x9e7e7fc  Failed start output
WARNING  listen.player.fadebin.StreamBin     stream "filename.mp3" already blocked

```

obviously with "filename.mp3" being the actual filepath.

help? last night Listen would crash with a seg fault whenever I tried to play something, but now instead i'm getting this.

---

### Post by evanct on 2010-03-06
Ugh, also now rhythmbox crashes with a seg fault when I try to play something. Banshee also crashes on play, but with a different error:

```
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.

```

I just can't get a break..

---

### Post by RedSingularity on 2010-03-06
How about a player like VLC?  Can you play it in that?

---

### Post by evanct on 2010-03-06
Yeah, video players work fine.

---

### Post by RedSingularity on 2010-03-07
How about the hidden listen folders?  Try deleting them and trying again.  It is located in you home folder.  When in your home folder press "ctl+h" to show them.

---

### Post by evanct on 2010-03-07
There is no .listen folder..

---

### Post by RedSingularity on 2010-03-07
Well you could try a complete reinstall of Listen.  Not the usual uninstall done from synaptic package manager, i mean deleting every listen related file on the system.  Want to give that a try?

---

### Post by christopherbalz on 2010-12-31
A complete re-install (e.g., via Synaptic) worked to get it playing audio again - until I changed my track selection.  For now at least, switched back to Rhythmbox (10.04 LTS, 64-bit, up-to-date).

---

