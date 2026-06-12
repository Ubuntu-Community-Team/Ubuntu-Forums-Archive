---
title: "82845G Video problem...."
date: 2010-05-13
forum: Multimedia Software
---

### Post by NathanaelC on 2010-05-13
Hey!

This is my first post in ubuntu forums.....and I need help...

Here's the deal:

My parents have a 8 yr old computer, and they have been running linux for the last 2 years- our graphics card has been a nightmare.

It has not worked right....since we first installed 7.10.

in 9.04 it could still halfway play DVD's & videos(just barely).

No longer in 10.04- Mplayer, totem, xine & VLC die when you try to play a video- any video.

And here's what I get(in terminal):

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 89 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Little help??

---

### Post by quixote on 2010-05-15
It sounds like the newer versions are no longer working with your hardware.  Possibly they just need too much memory.  It may be worth trying a "lighter" version, like Xubuntu which takes much less memory.

Or you could reinstall whichever older version worked best with that hardware, although you say none of them were particularly good.  (If you do that, back up the whole /home directory, including hidden files, so that you don't lose all your settings and configs.  If you have /home on a separate partition -- always a good idea! -- then you don't need to worry.  Just be sure not to reformat that partition when you do the new install of the old version.)

---

