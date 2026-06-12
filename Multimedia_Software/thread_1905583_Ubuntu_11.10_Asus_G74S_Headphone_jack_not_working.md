---
title: "Ubuntu 11.10 Asus G74S Headphone jack not working"
date: 2012-01-07
forum: Multimedia Software
---

### Post by kpryde on 2012-01-07
The headphone jack is not working. Using alsamixer, the headphones show up as a box with [00] written in it, but they don't have the column showing their volume. Any help would be appreciated.

---

### Post by Kaladze on 2012-01-07
i think u have the same problem like me [http://ubuntuforums.org/showthread.php?t=1905268](http://ubuntuforums.org/showthread.php?t=1905268)

---

### Post by kpryde on 2012-01-07
> **Kaladze said:**
> i think u have the same problem like me [http://ubuntuforums.org/showthread.php?t=1905268](http://ubuntuforums.org/showthread.php?t=1905268)

Yep, we do. That screenshot looks the same. Hopefully someone can help us out.

---

### Post by kpryde on 2012-01-09
Alright, so this is what works for me:

Go to system settings -> sound -> output -> chose internal audio analog stereo. For connector choose Analog Speakers.

However, when you plug and unplug the headphones, connector switches back to "analog headphones" and you need to change it manually back to analog speakers.

---

