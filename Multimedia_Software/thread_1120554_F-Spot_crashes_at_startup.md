---
title: "F-Spot crashes at startup"
date: 2009-04-09
forum: Multimedia Software
---

### Post by mjertin on 2009-04-09
Hi!

I have a problem with F-Spot: everytime I try to open it it crashes and immediately closes again.

I have tried several re-installs or complete removals and then installs, and I also deleted a lot of remaining F-Spot files (like ~/.gnome2/f-spot or /usr/share/app-install/desktop/F-Spot Photo Manager etc...).

When I start it through terminal I receive following error:

```

xyz@xyz-laptop:~$ f-spot
[Info  11:14:05.156] Initializing DBus
[Info  11:14:05.247] Initializing Mono.Addins
[Info  11:14:05.387] Starting new FSpot server

(f-spot:23334): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 337 error_code 1 request_code 143 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Anyone experienced similar behaviour?

Thank you!
mjertin

---

### Post by xc3RnbFO8P on 2009-04-09
Read this:
[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/297406]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/297406")

---

