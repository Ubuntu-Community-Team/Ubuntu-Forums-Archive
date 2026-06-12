---
title: "Webcam needs sudo"
date: 2011-02-11
forum: Multimedia Software
---

### Post by hornetster on 2011-02-11
Hopefully a simple answer, but can't find a solution searching.
Trying to run a Logitech Quickcam Express webcam, and works perfectly if you: sudo cheese for example, but won't work as a standard user.
Assuming that it is a "group" thing...?
Thanks, John.

Ubuntu 10.10 x86

---

### Post by hornetster on 2011-02-11
Worked it out: sudo chmod 777 /dev/video0

John.

---

