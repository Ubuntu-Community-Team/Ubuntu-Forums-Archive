---
title: "Banshee: &quot;GStreamer resource error: Failed&quot;"
date: 2008-04-11
forum: Multimedia &amp; Video
---

### Post by SomeGuyDude on 2008-04-11
I get that error when I run the banshee alpha via the terminal. That's my output. I'm wondering if this is why I can't use Exaile as well.

```
crew@crew-laptop:~$ banshee-1
[Info  00:08:51.192] All services are started 2.330081s
** (Nereid:30433): DEBUG: bp_stop: setting state to GST_STATE_NULL
[Error 00:08:53.894] GStreamer resource error: Failed

crew@crew-laptop:~$ 
```

This is all with Hardy, by the way, if that makes a difference.

---

### Post by SomeGuyDude on 2008-04-11
Annnnnybody?

---

### Post by flickerfly on 2008-05-07
Getting the same thing...

---

### Post by flickerfly on 2008-05-07
Posted a bug:

[http://bugzilla.gnome.org/show_bug.cgi?id=532031](http://bugzilla.gnome.org/show_bug.cgi?id=532031)

---

### Post by EyeFlys on 2008-05-13
Getting this too...very annoying.

EDIT: Also getting it with 1.0b1 from SVN

---

### Post by bigstras on 2008-06-13
though I am sure that after 4 weeks of not listening to music you have either gone insane or changed media players or (gasp!) switched to windows to use itunes, I just ran into this same problem and figured I'd refer anybody with this same problem in the future to [HyperAir's Solution]("http://bugzilla.gnome.org/show_bug.cgi?id=532031#c2")
This worked perfectly after a reboot and now i'm rockin out once again.

---

