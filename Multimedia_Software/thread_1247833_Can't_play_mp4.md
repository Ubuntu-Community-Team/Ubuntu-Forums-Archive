---
title: "Can't play mp4"
date: 2009-08-23
forum: Multimedia Software
---

### Post by tim1970 on 2009-08-23
I am trying to play a MP4 file.  When I attempt to open the file in Totem, it just pauses for a second, and then totem completely closes.  No error messages or anything.  Does anybody have any suggestions?  I am running Ubuntu 9.04.  I thought I had all the codecs, but apparantly something is still missing.


Thanks

---

### Post by ajgreeny on 2009-08-23
Use the terminal to play it with ```
totem filename.mp4
``` and see if any error messages appear.

---

### Post by tim1970 on 2009-08-23
Here is the error message.  I can't play any type of file,not just mp4

house@house-desktop:~$ totem
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 88 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
house@house-desktop:~$

---

### Post by ajgreeny on 2009-08-24
So, it's not a codec problem at all, by the sounds of it.  I suggest you uninstall totem-gstreamer and try again with totem-xine, which I think is much better than the gstreamer version.  A reinstall of the totem-common may also help, as it appears that there is a problem with your current package.

---

### Post by tim1970 on 2009-08-24
Well, I tried uninstalling everything and then re-installing totem-xine.  The same problem happened.  Here is the error message.  Any ideas?


Thanks

house@house-desktop:~$ totem-xine
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem-xine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 93 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
house@house-desktop:~$

---

### Post by mc4man on 2009-08-24
Try this, in a terminal
```
gstreamer-properties
```
Then under the video tab, expand Default Output and choose 
X Window System (No Xv)

( As noted, totem-xine is a better choice for a totem video player. make sure this is installed 
libxine1-ffmpeg


Edit;
gstreamer-properties ( Multimedia systems Selector) is one of several config tools disabled (not visible) the in the main menu by default.
Run in terminal, alacate ,(edit menus)  to see what's available. (edit menus itself is also disabled as a visible menu item

Seems a bit over cautious for some of the more useful ones

---

