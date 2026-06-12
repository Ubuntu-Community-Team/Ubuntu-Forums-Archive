---
title: "[SOLVED] Error trying to load GStreamer"
date: 2008-06-24
forum: Multimedia Software
---

### Post by soloman498 on 2008-06-24
While trying to load GStreamer ffmpg video plugin a box popped up with the message:

An error occured
The following details are provided:

E:dpkg was interrupted,you must manually
run 'dpkg_ _configure-a' to correct the problem.
E:_ cache-> open()failed,please report.

AS A Newby Can anybody help me with what to do?

---

### Post by cozmicharlie on 2008-06-24
Open a terminal and type or cut and paste the following:

```
sudo dpkg_ _configure-a
```

It will ask you for your password - just type in your password and wait until it is done.  Then go back into Synaptic and install gstreamer.

Enjoy!

---

### Post by soloman498 on 2008-06-24
I tried that but got this message:patrick@patrick-desktop:~$ sudo dpkg_ _configure-a
sudo: dpkg_: command not found

---

### Post by cozmicharlie on 2008-06-24
Didn't notice this but the command should be:

sudo dpkg --configure -a

not 

sudo dpkg _ _configure -a

---

### Post by soloman498 on 2008-06-27
thankyou.amended command fixed it.

---

