---
title: "Banshee crashes probably due to XAA"
date: 2009-06-19
forum: Multimedia Software
---

### Post by neo.patrix on 2009-06-19
My Banshee version :

I am using latest banshee verion from PPA, [Banshee-Team]("http://ppa.launchpad.net/banshee-team/ppa/ubuntu")

XAA :

I have the (in-famous) ATI X1300 card which works with OpenSource driver on Jaunty, but I had strange flickering on my screen from right-top to right-bottom. There is a bug report about this, the solution is to provide option in xorg.conf "AccelMethod" as "XAA" , guessing "EXA" is default the cause of trouble.

After changing to XAA, although my system loads very slowly then usual, there are no major performance problems once logged-in. 

Trouble :

Now Banshee used to play video-files properly before, I changed to "XAA". Once, I changed to XAA, Banshee crashes when I try to play  (.flv, .avi) vedio files. Probably, the crash is related to XAA, although it seems far-fetched. Same files play properly in VLC.

Here is the crash report

> 
(Banshee:21374): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window
The program 'Banshee' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 107 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)



If someone can please confirm problem or offer solution. Thanks in advance. (Changing to EXA is a solution, but XAA fixes flickering problem :), which is very prominent when using Firefox)

Other option is downgrading banshee. I have already tried that but I still get crashes. The previous version 1.4.3-3ubuntu2 ocassionaly used to give me strange "chipping"  sound when trying to play vedio, so I had changed to 1.4.3~hyper1+jaunty1.

---

