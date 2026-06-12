---
title: "Playback problem with Totem on Hardy Heron"
date: 2008-05-28
forum: Multimedia Software
---

### Post by Paresh on 2008-05-28
I seem to have an unusual problem playing video files:-

When playing an avi (mp4, divx etc) file, totem will launch and before playback will exit.

Running from terminal produces this error message

> The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 75 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
paresh@paresh-laptop:~$ 


vlc does something similar, but Kaffeine has sound and no video.

The strange thing is that with kaffeine running totem and vlc both work fine (sound and video).

I'm running Ubuntu 8.04 on a Toshiba Tecra A9 with advanced desktop settings enabled.  I also have installed medibuntu for the additional codecs.

Finally, this worked well on 7.10, so something appears to have been broken in 8.04.

Any help would be appreciated.

---

