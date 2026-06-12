---
title: "Newbie help translating gxine error message"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by papajack on 2007-03-09
I've been using linux for a little over a month. Everything has worked as advertised (with a little research and patience). I still very lost but willing to learn.

[B]When I start gxine I receive this in the terminal:
[/B]
t```
buss@ubuntu:~$ gxine&
[1] 15354
tbuss@ubuntu:~$ 
(gxine:15354): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(gxine:15354): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
xine-lib: error: The xine engine failed to start.: No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

[1]+  Done                    gxine
tbuss@ubuntu:~$ 
```

[B]When I exit out of gxine, I receive this message in the terminal:
[/B]
```
tbuss@ubuntu:~$ gxine exit
server: connected to existing gxine instance.
server: write error: Broken pipe
tbuss@ubuntu:~$ playlist_add: MRL=file:///home/tbuss/exit
CDROMREADTOCHDR: Input/output error
WARN: open (/dev/cdrom): No medium found
server: read error 123
xine-lib: error: File not found::  file:///home/tbuss/exit

(gxine:13927): Gdk-CRITICAL **: gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed

(gxine:13927): Gdk-CRITICAL **: gdk_window_move_resize: assertion `GDK_IS_WINDOW (window)' failed
xine-lib: error: The xine engine failed to start.: No input plugin was found.
Maybe the file does not exist or cannot be accessed, or there is an error in the URL.

```

**When I try to play an avi file from a network share (Windows) I get this:**

```
tbuss@ubuntu:~$ 
(gxine:16298): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(gxine:16298): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?

(gxine:16298): libgnomevfs-WARNING **: Failed to create service browser: Bad state


(gxine:16298): libgnomevfs-WARNING **: Failed to create service browser: Bad state


(gxine:16298): libgnomevfs-WARNING **: Failed to create service browser: Bad state


(gxine:16298): libgnomevfs-WARNING **: Failed to create service browser: Bad state


```

When I go to file-->open-->network servers-->windows network-->workgroup-->host-->avi file The file loads in gxine and it says it's buffering. But I have all these messages in the terminal. The file never plays though.
Also, when I try a second time to start gxine and navigate to the network share, the Windows machine is no longer listed in the network, when it was there a moment earlier?

---

### Post by ssavelan on 2007-03-10
try:

 sudo apt-get install libxine-extracodecs

if you do not already have it.

Then.. try to play the file again.

Does this happen with many files or just one?

---

### Post by springnuts on 2007-11-17
Hi, and may thanks for this which sorted out my issue too - 

Regards

Simon

---

### Post by jslmg on 2008-01-09
When I run sudo apt-get install libxine-extracodecs, I get this output:

```
~$ sudo apt-get install libxine-extracodecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine1-ffmpeg
E: Package libxine-extracodecs has no installation candidate
```

---

