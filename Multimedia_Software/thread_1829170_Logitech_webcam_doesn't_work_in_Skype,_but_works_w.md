---
title: "Logitech webcam doesn't work in Skype, but works with Cheese"
date: 2011-08-20
forum: Multimedia Software
---

### Post by JGT on 2011-08-20
Hi

I'm using a basically vanilla Lubuntu 11.04 

My Logitech E 3500 webcam works fine with Cheese.

I have just installed Skype, but my voice isn't picked up on the test call, and no video either (the webcam light remains off). I've tried logging off and into Skype.

Any ideas?  Thanks

---

### Post by sanderd17 on 2011-08-20
see this thread for video (please read the whole thing).

[http://ubuntuforums.org/showthread.php?t=1759012](http://ubuntuforums.org/showthread.php?t=1759012)

---

### Post by JGT on 2011-08-20
That's didn't work. Skype didn't launch afterwards.

I mv-ed /usr/bin/skype back and Skype launches again, but still no webcam.

---

### Post by JGT on 2011-08-20
I tried the suggestion on post #5, but it didn't work .Skype launched fine, but no webcam recognised.

---

### Post by no2498 on 2011-08-20
? you try this yet
in a terminal

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by JGT on 2011-08-20
Thanks. Tried it, rebooted, works now.

John

---

