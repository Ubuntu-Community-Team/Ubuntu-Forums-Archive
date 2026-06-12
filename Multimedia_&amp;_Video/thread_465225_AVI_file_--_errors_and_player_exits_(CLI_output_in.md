---
title: "AVI file -- errors and player exits (CLI output included)"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by eentonig on 2007-06-05
Anybody knows what these errors point to?

It's an .avi file and an equally named .srt file is in the same folder. When I try to open those files (I have several), the players (vlc, Xine, movie player) start up and exit abruptly.

The files are ok, because a colleague could open them on his pc.

> rfonteyn@ubuntu:/media/disk/MOVIE/Battlestar Galactica Season 1$ vlc Battlestar\ Galactica\ \(2003\)\ -\ s01e02\ -\ Water.avi
VLC media player 0.8.6 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85



rfonteyn@ubuntu:/media/disk/MOVIE/Battlestar Galactica Season 1$ gxine  Battlestar\ Galactica\ \(2003\)\ -\ s01e02\ -\ Water.avi
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
CDROMREADTOCHDR: Input/output error
WARN: open (/dev/cdrom): No medium found
[mpeg4 @ 0xb70f68b4]frame skip 8
[mpeg4 @ 0xb70f68b4]frame skip 8
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 390 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
rfonteyn@ubuntu:/media/disk/MOVIE/Battlestar Galactica Season 1$ 

---

### Post by eentonig on 2007-06-05
Never mind. It was Beryl.

Strange though, because I'm able to play avi's when Beryl is running. Just these aren't possible.

---

