---
title: "Microsoft VX-3000 webcam not detected by Ubuntu"
date: 2011-09-02
forum: Multimedia Software
---

### Post by Zisis19992 on 2011-09-02
Hello, i have compatibility problems with my webcam... In Skype for example it shows nothing... What can i do to solve this problem? :)

---

### Post by no2498 on 2011-09-02
open a terminal copy and paste

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype       click enter

---

### Post by Zisis19992 on 2011-09-02
Thank you VERY VERY MUCH my friend! I had to fix it.... :):guitar:

---

### Post by Zisis19992 on 2011-09-02
One more question... When i tap ''skype'' in the terminal, Skype starts, but the webcam is still not working... :(

---

### Post by no2498 on 2011-09-03
install guvcview see if it works in it
its in your package manager

---

### Post by Zisis19992 on 2011-09-03
Yes, it works with this, but the camera works is Skype only with the command that you gave me... If i enter directly to Skype, nothing happens... (thanks for your answer :) )

---

### Post by no2498 on 2011-09-04
ive only seen how to make it a bin/bash file 1 time
its in an old skype thread

---

