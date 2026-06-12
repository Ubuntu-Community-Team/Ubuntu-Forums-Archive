---
title: "Editing /etc/X11/xorg.conf ??"
date: 2006-01-06
forum: Multimedia &amp; Video
---

### Post by kudu on 2006-01-06
Is there any special command to run after editing /etc/X11/xorg.conf ? I hashed out "GLcore" and "dri" from the module section and I want to know if I need do anything else ?

Trying to figure out why OpenGL example code runs a million miles an hour. I refer to the classic rotating Triangles etc. Should rotate slowly but they're spinning like crazy. glxgears runs fine, getting 12000 +- fps, gears turn slowly.
But example OpenGL code isn't right for some reason.

kudu...out

---

### Post by gerbman on 2006-01-06
[QUOTE=kudu]Is there any special command to run after editing /etc/X11/xorg.conf ? I hashed out "GLcore" and "dri" from the module section and I want to know if I need do anything else ?

Trying to figure out why OpenGL example code runs a million miles an hour. I refer to the classic rotating Triangles etc. Should rotate slowly but they're spinning like crazy. glxgears runs fine, getting 12000 +- fps, gears turn slowly.
But example OpenGL code isn't right for some reason.

kudu...out[/QUOTE]

I think all you need to do is restart x. I would back up your xorg.conf just in case, then hit ctrl+alt+backspace to restart x. If x won't restart properly, just move the backup file to /etc/X11/xorg.conf and restart x again.

---

### Post by kudu on 2006-01-06
That's what I though and that's how I've been operating for awhile now. Just wondered is all. Thanks!

---

