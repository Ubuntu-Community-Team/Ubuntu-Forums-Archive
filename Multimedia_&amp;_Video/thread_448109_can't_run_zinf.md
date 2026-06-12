---
title: "can't run zinf"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by Eredeath on 2007-05-18
when i try to run zinf (after dwlding it from the synaptic package manager) i get this:
```
eredeath@eredeath-laptop:~$ zinf

(<unknown>:6354): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:6354): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:6354): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:6354): Gdk-CRITICAL **: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 325 error_code 8 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```
I looked on the website and saw that it needs to have "platform x" does anyone know what that is or how to get it?
if anyone can help me i would appreciate it
Thanks in advance

---

### Post by orthopod on 2007-11-12
Exactly the same error message.  And I have seen at least 3-4 other help messages with the same error.

---

### Post by AnRkey on 2008-02-14
Has anyone figured this out yet?

---

