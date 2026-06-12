---
title: "Ubuntu Quits (Distro 13.04)"
date: 2013-07-07
forum: Multimedia Software
---

### Post by DoctorVell on 2013-07-07
TOPIC CORRECTION: VLC QUITS NOT UBUNTU QUITS!

Recently I was unable to play any of my videos through VLC...I have been doing my usual daily updates but now it just won't work.  I can play my MP3's with no problem but just the video files won't work anymore.  I did NOT change any configuration in the program and used to use it for my default media player.  It worked for all the video types before too.  Here's what I did via command line.  NOTE: I did try to un-install it and re-install it and that did NOT work.
[INDENT][B]doctorvell@DoctorVell:~/Downloads$ vlc a.mp4
VLC media player 2.0.6 Twoflower (revision 2.0.6-0-gbe9623c)
[0x1e48108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x7fc6a8001268] xcb_xv vout display error: no available XVideo adaptor
The program 'vlc' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 12 error_code 1 request_code 153 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[/B][/INDENT]

---

### Post by mc4man on 2013-07-07
First I'd reboot & check again. If still borked - 

If you go to ~/.config/vlc there are 2 files as in screen. Delete or mv both to a .bak, then try vlc again
(this will return vlc to install defaults.

If still no good the error concerns video driver.  You could try opening vlc > Tools >Preferences > Video & pick a specific video output
(default is auto, preferred is XV, 2nd choice OpenGL, worst is X11, some aren't usable

---

### Post by DoctorVell on 2013-07-11
Well, with my latest update it updated the Adobe Flash thing and it now works fine :) :) :) :)

---

