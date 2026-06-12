---
title: "Gxine Error"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by adolfofoliaco on 2007-08-11
Hello  I have this error on Gxine 

adolfo@adolfo-laptop:~$ gxine
/home/adolfo/.themes/OSY/gtk-2.0/gtkrc:208: Unable to locate image file in pixmap_path: "Lines/line-v.png"
/home/adolfo/.themes/OSY/gtk-2.0/gtkrc:211: Background image options specified without filename
/home/adolfo/.themes/OSY/gtk-2.0/gtkrc:1556: Unable to locate image file in pixmap_path: "Menu-Menubar/1menubar.png"
/home/adolfo/.themes/OSY/gtk-2.0/gtkrc:1559: Background image options specified without filename

** (gxine:6097): WARNING **: Invalid borders specified for theme pixmap:
        /home/adolfo/.themes/OSY/gtk-2.0/Range/null.png,
borders don't fit within the image
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?

** (gxine:6097): WARNING **: Invalid borders specified for theme pixmap:
        /home/adolfo/.themes/OSY/gtk-2.0/Buttons/button-default.png,
borders don't fit within the image
  sysname: Linux
  release: 2.6.20-16-generic
  machine: i686
X-Video Extension version 2.2
video_out_xv: Xv image format: 0x32595559 (YUY2) packed
video_out_xv: this adaptor supports the yuy2 format.
video_out_xv: Xv image format: 0x32315659 (YV12) planar
video_out_xv: this adaptor supports the yv12 format.
video_out_xv: Xv image format: 0x30323449 (I420) planar
video_out_xv: Xv image format: 0x59565955 (UYVY) packed
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 399 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

And when start I close .

Thanks

---

### Post by RomeReactor on 2007-08-11
Hi.
> The error was 'BadAlloc (insufficient resources for operation)'.
That's a very common error when using Desktop Effects (Compiz) or Beryl and trying to play a video file. If you *are* running either of those, try the solution in [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback").

By the other warnings it looks like Gxine can't find certain elements from your current theme, like buttons and window borders. Try using the Human theme, or another of the ones included with Ubuntu by default.

---

### Post by adolfofoliaco on 2007-08-12
ok I did but there nothing about Gxine

---

### Post by RomeReactor on 2007-08-12
Did you change the theme? if so, did the videos play afterwards?

---

### Post by adolfofoliaco on 2007-08-12
Yes I changed the theme, but the problems is that Gxine close every time that I Open it,

---

