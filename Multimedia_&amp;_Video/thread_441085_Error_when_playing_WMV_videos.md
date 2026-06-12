---
title: "Error when playing WMV videos"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by seelk on 2007-05-12
I get the following error when trying to play a gamespot HD video.  I have installed all restricted codecs and I'm able to play other video formats such as mpeg and avi.  Moreover, the Totem Firefox plugin doesn't seem to work for WMV videos either...

```
$ totem 169_halo3_gp_08_x360_051107.wmv 
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 48 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```
Any ideas?  I'm using Ubuntu Feisty 7.04.

---

### Post by DizzyTech on 2007-06-13
I hate to say this, but turn off Desktop Effects (Compiz or Beryl).  That fixes it.

---

