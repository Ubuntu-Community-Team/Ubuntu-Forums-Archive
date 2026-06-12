---
title: "[SOLVED] All players crash when i play wmv files"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by Philipk on 2007-09-12
This is my first post on the forum, and the first time that i am using linux so if there is anything i can do to help you help me, please tell me.
i was playing all video files just fine but then today all of a sudden  i cant play wmv files.
totem and vlc crashes while Mplayer says:

Fatal error!
Error opening/initializing the selected video_out(-vo) device

running vlc through the terminal it says:

X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84

and totem says:
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 48 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

i have installed w32codecs, didnt help tho.

well thanks for the help.

update:
found out that i can play low res wmv files, but as soon as it gets close to hd, it crashes

---

### Post by mikeize on 2007-09-12
I'm having the same problem with DVDs.  I tried a real and a burned DVD.  Everything that tries to open it crashes immediately.

-mike

edit:  I can play any vid file off my hard drive, but DVD's crash every program.  The drive is mounted, and I can browse the DVD files, but can't play them.

---

### Post by reckless2k2 on 2007-09-12
i know there's a bit about tweaking a few things depending on the video driver (like ATI) and if your using desktop effects like compiz......

see if this helps...do a little reading..

[http://easylinux.info/wiki/Ubuntu:Feisty](http://easylinux.info/wiki/Ubuntu:Feisty)

---

### Post by Philipk on 2007-09-13
well thanks for the help, i did what it said on:

[http://easylinux.info/wiki/Ubuntu:Feisty#What_to_do_if_Video_players_crash_while_using_Beryl](http://easylinux.info/wiki/Ubuntu:Feisty#What_to_do_if_Video_players_crash_while_using_Beryl)

and it worked even tho i didnt use dekstop effects or beryl

---

### Post by reckless2k2 on 2007-09-13
mark is as SOLVED baby!!! 

glad to be of help

---

