---
title: "Ubuntu 'motion' program"
date: 2010-09-27
forum: Multimedia Software
---

### Post by Joshun on 2010-09-27
Please could somebody help me with this. I am trying to set up the 'motion' program to capture video from a webcam, however by default the program simply dumps loads of jpeg files into the home directory. I would like the program to encode a video file (don't mind what codec) so that it can be played back correctly, without it putting any jpegs anywhere. 

Joshun

---

### Post by Joshun on 2010-09-27
Also note: we need to do this to find out who is vandalising our car.

---

### Post by Joshun on 2010-09-27
Solved  - the motion program wasn't recognising the config (/etc/motion/motion.conf) file because the permissions were set wrong. Changing it from none to read only on the 'others' group worked.

---

