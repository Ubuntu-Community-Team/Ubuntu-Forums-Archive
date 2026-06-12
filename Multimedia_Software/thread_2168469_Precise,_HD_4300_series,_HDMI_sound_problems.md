---
title: "Precise, HD 4300 series, HDMI sound problems"
date: 2013-08-18
forum: Multimedia Software
---

### Post by james29 on 2013-08-18
Hi I am new to this and first post. Most of the problems I have encountered I usually check the forums and play around and it usually works...just not this...

I have the Ubuntu 12.04., ATI Radeon HD 4300 Series.  I have surfed all day in the forum and still haven't gotten the HDMI sound to work...

I have installed the new kernel (still don't know what that is...), installed the pulseaudio and went to configuration and set the HDMI...
Went to config the file of pulseaudio so the it takes Hdmi by default (not sure how to exit or save, tried typing ^X does't work, I closed the terminal and "killed it", not sure if I am doing it right), tried to install the newest driver of Ati but it just freezes the screen and doesn't continue...

Anyone that can guide me step by step ? I would be really appreciated.

---

### Post by Yellow Pasque on 2013-08-18
@jamees29: [https://help.ubuntu.com/community/RadeonDriver#HDMI_Audio](https://help.ubuntu.com/community/RadeonDriver#HDMI_Audio)

---

### Post by QIII on 2013-08-18
Moved to its own thread.

---

### Post by james29 on 2013-08-18
Hi, 

Thanks a lot for the reply.

Doing workaround 1, it displays this

I typed in edit /etc/default/grub and pressed entered 

Watning: unknow mime-type for "/etc/default/grub" -- using "application/octet-stream"
Error: no write permission for file "/etc/default/grub"

What does that mean?

---

### Post by Yellow Pasque on 2013-08-18
```
gksu gedit /etc/default/grub
```

---

### Post by james29 on 2013-08-18
Thank you very much! My HDMI sounds works now! I am so happy. Makes my whole day surfing the forum feels a bit wasted...but nvm that. :p

---

