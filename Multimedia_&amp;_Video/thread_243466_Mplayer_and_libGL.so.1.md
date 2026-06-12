---
title: "Mplayer and libGL.so.1"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by Gryphin on 2006-08-25
Mplayer wont start. It says:

mplayer: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


Yesterday everything was OK.

---

### Post by croak77 on 2006-08-25
What video driver are you using, mesa, nvidia, fglrx? Are you using xgl?

---

### Post by Gryphin on 2006-08-25
fglrx, no not Xgl.

---

### Post by Mujaheiden on 2007-11-26
Dont kow what it was, but > sudo ln -f /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
fixed it.

---

