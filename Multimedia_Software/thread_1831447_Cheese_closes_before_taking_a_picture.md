---
title: "Cheese closes before taking a picture"
date: 2011-08-23
forum: Multimedia Software
---

### Post by source.decay on 2011-08-23
Hello, I was trying to use Cheese today to take a picture using my built in web camera on my laptop.  I am able to start the program and when it goes to take a picture, the program counts down and then quits.

When I run from the terminal the error I receive is:

> cheese: ../../src/xcb_io.c:140: dequeue_pending_request: Assertion `req == dpy->xcb->pending_requests' failed.
Aborted


Any help, please?

---

### Post by no2498 on 2011-08-24
see if this helps
in a terminal type

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese click enter

if it helps you need to make a /bin/bash file for it

---

### Post by source.decay on 2011-08-24
That worked perfectly!  Thank you!  Why is that library not loading?  Do you know?

---

### Post by no2498 on 2011-08-25
sorry but i do not know why it dont load

---

