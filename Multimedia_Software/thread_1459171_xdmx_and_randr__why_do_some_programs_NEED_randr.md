---
title: "xdmx and randr / why do some programs NEED randr?"
date: 2010-04-21
forum: Multimedia Software
---

### Post by andreas.kotowicz on 2010-04-21
I'm currently playing around with xdmx so I can use 2 computers and 3 screens to make 1 big desktop. Everything works fine except that I can not run programs like gedit, nautilus, etc ...
I always get the following error message:

```

$ gedit
Xlib:  extension "RANDR" missing on display ":1.0".
The program 'gedit' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 398 error_code 11 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```I'm running xdmx with the following parameters:
```

#!/bin/bash
startx -- \
/usr/bin/X11/Xdmx :1 \
-configfile  xdmx.conf                      \
-config  quad_config                        \
-ignorebadfontpaths \
+xinerama \
-input :0

```Spending some time on google I found out that xinerama will disable RANDR. So far so good. But why do some programs seem to NEED randr (gedit, nautilus) and other don't?
E.g: gnome-terminal and firefox will complain that RANDR is missing but will nevertheless run:

```

$ gnome-terminal
Xlib:  extension "RANDR" missing on display ":1.0".

```Is there a way that I can get gedit, nautilus and other programs to work? Can I tell these programs to not try to use RANDR?

---

