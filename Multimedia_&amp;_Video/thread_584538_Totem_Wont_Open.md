---
title: "Totem Wont Open"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by MasterRoshi on 2007-10-21
hey guys. totem wont open after running this terminal line to install codecs so my ATI X1400 wont distort colors.

here is what was told to me in a forum to paste in terminal:


"sudo aptitude install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 totem-xine"


i tried opening totem manually, through terminal, but i get the following error:


(totem:10763): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 42 error_code 8 request_code 140 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


i have no clue what to do. im running Gutsy Gibbon right now, clean install with ATI restricted drivers running...

someone help please! thanks!

---

### Post by guillepb on 2007-10-22
That error has been reported here in the forums before, and there is a bug open in launchpad about it:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/130696](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/130696)

But no one seems to be paying much attention to it, honestly :(

---

