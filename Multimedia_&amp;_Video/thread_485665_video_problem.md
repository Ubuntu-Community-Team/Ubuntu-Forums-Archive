---
title: "video problem"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by Sipheren on 2007-06-27
Hey,

I would really like some help on this one, don;t want to have to re-install.

I have been playing around with drivers and beryl, After no success I uninstalled beryl and the fglrx driver and started from scratch reinstalling the fglrx driver and not worrying about beryl. Not when ever I open a media player I get the following.

```
david@david-ubuntu:~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 42 error_code 8 request_code 141 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
david@david-ubuntu:~$ xine
This is xine (X11 gui) - a free video player v0.99.5cvs.
(c) 2000-2006 The xine Team.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  14 ()
  Serial number of failed request:  2050
  Current serial number in output stream:  2050
david@david-ubuntu:~$ 

```

---

