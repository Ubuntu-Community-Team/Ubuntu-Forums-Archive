---
title: "System timer resolution too low for Rosegarden to work. Need help!"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by oliverb4ss on 2007-05-10
When I start up Rosegarden 1.4, it says that my system timer resolution is too low.

The exact error message is as follows:

Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean that you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.

So, what can I do to fix this?

Thanks :)

---

### Post by mohnkern on 2007-05-10
See [https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime) to install a kernel with the timing you need.

---

### Post by eric71 on 2007-05-11
The lowlatency kernel in the feisty repositories will also do the trick.

---

### Post by mohnkern on 2007-05-11
I'd installed the low latency ones, but hadn't tried them yet.

---

