---
title: "cannot play video in totem, or VLC, or Mplayer"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by daverich on 2007-05-30
I get this error trying to run a movie in totem -

dave@dave-desktop:~$ totem '/home/dave/Desktop/wg_gdo_1.mpg' --sync
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 44 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I've tried re-installing the program, no difference though.

Any ideas?

I'm pretty sure it used to work heh.

Kind regards

Dave Rich

---

### Post by daverich on 2007-05-30
fixed.

Just needed to turn beryl off and use metacity.

Kind regards

Dave Rich

---

### Post by celticbhoy on 2007-05-31
Same problem, Same solution, does anyone know why video files wont play with beryl???

---

### Post by toobuntu on 2007-06-15
fix video rendering with certain apps that show only a black screen when run under Beryl:
1. set VLC->Settings->Preferences->Video->Output modules->X11 video output
2. set Mplayer->Preferences->Video->X11
3. for Mplayer firefox plugin: MAY need to edit /etc/mplayer/mplayer.conf:
replace line near top that says: #-vo=xv, with this: -vo=gl #changes video output driver from xv to gl.  (n.b.: at least one person reported not being able to resize windows if using -vo=x11)
4. Xine Movie Player: just seems to work w/o needing to be reconfigured
5. Totem Movie Player - don't know how to fix this app for use under Beryl

---

