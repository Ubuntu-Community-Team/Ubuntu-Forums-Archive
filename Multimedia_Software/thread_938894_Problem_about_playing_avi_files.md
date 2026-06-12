---
title: "Problem about playing avi files"
date: 2008-10-05
forum: Multimedia Software
---

### Post by bonjurkes on 2008-10-05
Hello,

I just installed the new ubuntu 8.10. And i was trying to play an avi file to see if there is a problem about graphic card driver.

So i installed the codecs, when i try to play the avi file, player window opens than disappears. I tried with vlc and xine. When i give command from terminal it says

> [????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85
E: thread-posix.c: Assertion 'pthread_setspecific(t->key, userdata) == 0' failed at pulsecore/thread-posix.c:194, function pa_tls_set(). Aborting.


Can someone help me about this problem please?

---

### Post by xc3RnbFO8P on 2008-10-05
In VLC preference> output modules> try to change **default** to **X11** 
(check the **advance options** box).

---

### Post by fitzdragon on 2008-10-06
thanks for that , vlc crashing was driving me mad for the last 24 hours

---

