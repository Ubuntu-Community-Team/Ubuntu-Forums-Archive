---
title: "quadrapassel closed when run"
date: 2010-09-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mperry on 2010-09-16
From the games menu, nothing happens when I click on it. From a terminal, I get this:

(quadrapassel:5309): ClutterGLX-CRITICAL **: Unable to make the stage window 0x5000005 the current GLX drawable

(quadrapassel:5309): ClutterGLX-CRITICAL **: Unable to make the stage window 0x5000006 the current GLX drawable

(quadrapassel:5309): ClutterGLX-CRITICAL **: Unable to make the stage window 0x5000005 the current GLX drawable

Gdk-ERROR **: The program 'quadrapassel' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 69 error_code 9 request_code 137 minor_code 12)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
aborting...
Trace/breakpoint trap

Anyone else seeing this with the game?

---

### Post by SevenMachines on 2010-09-16
yes, me too
[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-games/+bug/639845](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-games/+bug/639845)

---

### Post by mperry on 2010-09-16
This was fixed with the latest updates. Back to something meaningful :-) Thanks ubuntu. You gave me back my falling blocks of all different colors.

---

