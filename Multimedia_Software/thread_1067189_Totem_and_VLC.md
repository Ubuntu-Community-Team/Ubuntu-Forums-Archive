---
title: "Totem and VLC"
date: 2009-02-11
forum: Multimedia Software
---

### Post by belitos on 2009-02-11
Hello guys,im kinda new some linux so here is my problem

when i try to play anything with the totem midia player or VLC it closes!!!!
whats the problem?
thanks!

---

### Post by Simian Man on 2009-02-11
Try running vlc from the command line and see if gives you any warning messages.  Run the terminal under Applications->Accessories and type 'vlc' at the prompt.  Then try to open a media file and when it crashes look for the command line output if there is any.

---

### Post by belitos on 2009-02-11
> **Simian Man said:**
> Try running vlc from the command line and see if gives you any warning messages.  Run the terminal under Applications->Accessories and type 'vlc' at the prompt.  Then try to open a media file and when it crashes look for the command line output if there is any.
i did it with totem,here it is

```
** (totem:13398): DEBUG: Init of Python module
** (totem:13398): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:13398): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:13398): DEBUG: Creating Python plugin instance
** (totem:13398): DEBUG: Init of Python module
** (totem:13398): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:13398): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:13398): DEBUG: Creating Python plugin instance
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 47 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)



```

---

### Post by mc4man on 2009-02-11
Unfortunately a couple of useful setings menu's are disabled by default. One is 'multimedia systems selector' the other 'file management'

The video output for totem is in set in the first one.
Run this in a terminal and under the video tab for 'output' change from auto detect to the one with X11 in the line and see if that helps totem. 
If so, for vlc the setting is in (for vlc 0.9.4 (intrepid) tools -> preferences -> video and in the output dropdown choose x11.
```

gstreamer-properties
```

You could also see if restricted drivers are available in System -> Admin.


The other useful setting box is 'file management'

```
nautilus-file-management-properties
```


Both can be enabled in the main menu from 
```
alacarte
```

---

### Post by belitos on 2009-02-11
> **mc4man said:**
> Unfortunately a couple of useful setings menu's are disabled by default. One is 'multimedia systems selector' the other 'file management'

The video output for totem is in set in the first one.
Run this in a terminal and under the video tab for 'output' change from auto detect to the one with X11 in the line and see if that helps totem. 
If so, for vlc the setting is in (for vlc 0.9.4 (intrepid) tools -> preferences -> video and in the output dropdown choose x11.
```

gstreamer-properties
```

You could also see if restricted drivers are available in System -> Admin.


The other useful setting box is 'file management'

```
nautilus-file-management-properties
```


Both can be enabled in the main menu from 
```
alacarte
```

it works!!!!!!
thank you very much!

---

