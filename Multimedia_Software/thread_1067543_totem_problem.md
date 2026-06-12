---
title: "totem problem"
date: 2009-02-12
forum: Multimedia Software
---

### Post by bilalakhtar on 2009-02-12
when I open a media file from nautilus, totem opens for a second and closes. i was running it through the intrepid 32bit live cd and i m going to install ubuntu from it. my graphics card is ATI mobility radeon x1600. is there any fix available for this after I install ubuntu intrepid? i have noticed this problem is not there in hardy.

---

### Post by ad_267 on 2009-02-12
Try opening the file from the terminal (applications - accessories - terminal) and see what errors you get.

Eg:
```
totem "path/to/media/file.avi"
```

---

### Post by bilalakhtar on 2009-02-12
> **ad_267 said:**
> Try opening the file from the terminal (applications - accessories - terminal) and see what errors you get.

Eg:
```
totem "path/to/media/file.avi"
```

this is the output I got:-
** (totem:8161): DEBUG: Init of Python module
** (totem:8161): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:8161): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:8161): DEBUG: Creating Python plugin instance
** (totem:8161): DEBUG: Init of Python module
** (totem:8161): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:8161): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:8161): DEBUG: Creating Python plugin instance
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 73 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by bilalakhtar on 2009-02-15
ok, i dont know how but my prob got solved when I turned desktop effects off.

---

