---
title: "Cheese error"
date: 2013-10-27
forum: Multimedia Software
---

### Post by Otto-C on 2013-10-27
Ubuntu 12.04.4 fully up to date.
Nothing special installed.
Dell B110 1gb ram
VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
Cheese installed from Software Center.

Cheese error how to fix?
tia
otto-c

:~$ cheese

(cheese:5526): Gdk-WARNING **: The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadContext'.
  (Details: serial 153 error_code 169 request_code 153 minor_code 6)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

:~$

---

### Post by ajgreeny on 2013-10-27
I have never found cheese to be very useful; it would never manage to produce or save videos on my system when using 10.04 Lucid with gnome 2 desktop, so I replaced it with guvcview, which worked so much more successfully, and still does with my Xubuntu 12.04.

Give it a try if you can't get cheese working properly.

---

