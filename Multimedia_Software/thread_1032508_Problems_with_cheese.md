---
title: "Problems with cheese"
date: 2009-01-06
forum: Multimedia Software
---

### Post by electrocallejero on 2009-01-06
Cannot get cheese to work! I have a pandolin performance from system 76. I installed cheese but when I click on record video the whole application goes dark and I have to force quit + I will not let me take a photo. Could this be a bug in the program or is it that it just cannot find the webcam?

---

### Post by electrocallejero on 2009-01-06
> **electrocallejero said:**
> Cannot get cheese to work! I have a pandolin performance from system 76. I installed cheese but when I click on record video the whole application goes dark and I have to force quit + I will not let me take a photo. Could this be a bug in the program or is it that it just cannot find the webcam?

here is how it looks on screen

---

### Post by quip on 2009-01-06
It could be one of several things.  The first thing to do is list what kind of webcam you have (built-in, external?) and what make/model (Logitech/Quickcam, etc.?).

Also, it is usually a good idea to start a misbehaving app from the command line (Terminal)--many apps will give some good debugging messages.

Last, do you have desktop effects (fancy compiz stuff) turned on?  While debugging a graphical app, I would definitely turn it off if I had it on.

---

### Post by quip on 2009-01-06
BTW, I just noticed your double-post (starting two different thread for the same question).  I don't know if it was intentional or not, but it is usually considered bad form.

Try to delete the other one, if you can (it doesn't have any responses yet, anyway).

---

### Post by Hilko on 2009-01-22
> **electrocallejero said:**
> Cannot get cheese to work! I have a pandolin performance from system 76. I installed cheese but when I click on record video the whole application goes dark and I have to force quit + I will not let me take a photo. Could this be a bug in the program or is it that it just cannot find the webcam?

Got the same problem. Cannot record video. If I click on take photo i see a countdown, then a flash and hear the sound of a camera. However no photo. The app just goes dark and I have to force quit.

The terminal gives no info:
```
:~$ cheese
Killed

```

---

### Post by electrocallejero on 2009-02-17
This is the error I get when opening it from the command terminal.

(cheese:8407): GStreamer-WARNING **: pad source:src returned caps which are not a real subset of its template caps
libv4l2: error requesting 4 buffers: Device or resource busy


Not sure what it means?

---

