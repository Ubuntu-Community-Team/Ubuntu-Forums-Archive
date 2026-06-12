---
title: "Nvidia-settings and glxinfo crash"
date: 2008-12-19
forum: Multimedia Software
---

### Post by fjk8 on 2008-12-19
Hello, 

i have some problems with nvidia-settings and glxinfo.
When im trying to launch one of these i recive an error.
This is happend after im trying to install libdrm and mesa libraries which is needs to intel graphics driver.
Now im working on nvidia graphics card which work fine earlier (usb disk, nvidia in home, intel in work).

nvidia-settings :

```
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadLength (poly request too large or internal Xlib length erro'.
  (Details: serial 141 error_code 16 request_code 128 minor_code 17)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

glxinfo:

```

name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

```

Im trying 173 and 177 driver but im thinking this is not problem with driver....
I have proper resolution, working compiz...

---

### Post by fjk8 on 2008-12-21
Anyone ? 
Bug log: [http://intellinuxgraphics.org/download.html]("http://intellinuxgraphics.org/download.html")

---

