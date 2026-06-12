---
title: "Google Earth is causing a segmentation fault"
date: 2010-05-21
forum: Multimedia Software
---

### Post by AKADAP on 2010-05-21
Since upgrading to 10.04, Google Earth is causing a segmentation fault. 

I spent an hour at the google earth website failing to find out how to report a bug. Anyone know how to report a bug to google?

When run from a command line, I get this:

googleearth-bin: ../../src/xcb_io.c:549: _XRead: Assertion `dpy->xcb->reply_data != ((void *)0)' failed.
Google Earth has caught signal 6.

We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/user/.googleearth/crashlogs/crashlog-4bf6f443.txt

Please include this file if you submit a bug report will to Google.

I thought this might have something to do with OpenGL, because I had a problem with openGL on MythTV, but the games that use OpenGL in the games menu don't seem to have a problem.

---

### Post by mellery on 2010-06-27
I'm having this problem too with google earth.  My mythtv is working fine however.  Can anyone help please?

---

### Post by AKADAP on 2010-06-27
My solution was to use the open source drivers (just uninstall the proprietary driver) Has the added benefit that there is no tearing with MythTV

---

