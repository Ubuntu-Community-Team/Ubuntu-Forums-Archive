---
title: "All video-players except Mplayer and Democracy closes when opening files"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by kwaanens on 2007-04-19
I tried: Totem, VLC, Gxine. Tried Totem with an avi-file that Democarcy plays OK.
They all functioned correctly in Edgy.

Here's someoutput:

```
$ totem
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 44 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

VLC on a file in ~/Desktop (root-partition)

$ vlc 
VLC media player 0.8.6 Janus
[00000295] access_file access error: seeking too far
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86


```

What resources? 2gHz Intel Core2 Duo and 2 gigs of swap. / has 8 gigs unused. That can't be he problem. My system is snappy as h...

gst-inspect has:
"Total count: 140 plugins, 633 features"
as its last line (too long to post the whole thing.

- Ketil

---

### Post by kwaanens on 2007-04-19
Shutting down Beryl makes this work. This is a major bug! Only me?

- Ketil

EDIT: fixed. Had to change each movie player to X11 or something else. Now they work.

---

### Post by lukemack on 2007-04-22
can you please elaborate on the fix? in don't understand it, how do you change a player to x11 and what does that mean?

---

### Post by kwaanens on 2007-04-23
It means what module the players use to output video on your screen.

For gstreamer-apps: 
$ gstreamer-properties
Go to "Video", my choice is "X Window System (No Xv)"

VLC: Open VLC > Settings > Preferences > Video > Output modules. Check "Advanced options". My choice is "X11 Video Output"

Figuring out various other apps should be pretty easy. Try out the settings.

- Ketil

---

### Post by SanguineIllusion on 2007-04-23
Thank you SOOO much for this! I've been trying all kinds of fixes that i've been finding all over the internets to no avail. This is a major bug, i hope they fix it at some point. Now I can watch vids while still using beryl like the fancy gentleman that I am ;)

---

### Post by smac4president on 2007-04-30
Sweeeeeeeeeet.  This is a major bug.  Works in KDE but not in Beryl.  Setting VLC to X11 worked for me (not that I ever would have figured that out on my own).  I wonder if everyone has this problem?
Thanks though!

---

### Post by Andreiz on 2008-04-10
thx for the solution, worked like a charm

---

