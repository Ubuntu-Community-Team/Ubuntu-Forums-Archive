---
title: "Audio recorder with scheduling feature"
date: 2010-05-14
forum: Multimedia Software
---

### Post by rmcellig on 2010-05-14
I am a Mac user who has been using Audio Hijack Pro for many years. I use it to record radio shows from the station I work at. One of the nice features is that it has a built in scheduler that I use to record shows at different times and dates.

[http://www.rogueamoeba.com/audiohijackpro/](http://www.rogueamoeba.com/audiohijackpro/)

Is there anything similar for Ubuntu? I really hope so!!

---

### Post by tgalati4 on 2010-05-14
cron job, streamripper, arecord:

man cron
man crontab

sudo apt-get install streamripper
man streamripper

man arecord

!fancy.

sudo apt-get install tunapie
tunapie

Gui which allows recording of streams with a scheduler, requires streamripper.

---

### Post by rmcellig on 2010-05-14
Thanks tgalati4. So you are saying that if I install Streamripper or Tunapie, I should be all set?

---

### Post by tgalati4 on 2010-05-14
Install streamripper then install tunapie.

---

### Post by rmcellig on 2010-05-15
Does it matter by installing it in this order?

---

### Post by tgalati4 on 2010-05-15
No.

---

