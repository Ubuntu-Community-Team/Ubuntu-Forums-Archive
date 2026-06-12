---
title: "Webcam working in Cheese, not in Skype"
date: 2012-05-03
forum: Multimedia Software
---

### Post by dhkillian on 2012-05-03
Hi
Installed a Logitech HD C525 webcam this morning. Have got it working in Cheese,(albeit without sound), but can't get it to run with Skype at all. 
I'm running 12.04 LTS
Grateful for any help.

---

### Post by yankysunny on 2012-05-03
check in the settings of skype if it picks it up...otherwise reset the PC and try again

---

### Post by dhkillian on 2012-05-03
...tried it using GUVCview, it works perfectly, sound and picture. Not so in Skype.......and yes, I have rebooted!

---

### Post by dhkillian on 2012-05-03
Tried again.....after some messing around, I have found that if I start GUVCview before I start Skype, I can get sound on Skype, though no video. 
Anyone any ideas?

---

### Post by BicyclerBoy on 2012-05-03
Assuming 64 bit OS..
This info could be outdated..

Skype used to require the 32bit v4l library &/or older v4l1 library 

Try in terminal:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

References:
[http://community.linuxmint.com/tutorial/view/219](http://community.linuxmint.com/tutorial/view/219)

---

### Post by dhkillian on 2012-05-04
Many thanks!

Now working!!!

---

### Post by dhkillian on 2012-05-04
How do I mark this as resolved?

---

### Post by mörgæs on 2012-05-07
By using 'thread tools' in the top right corner.

---

