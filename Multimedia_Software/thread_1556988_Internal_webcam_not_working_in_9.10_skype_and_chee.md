---
title: "Internal webcam not working in 9.10 skype and cheeese"
date: 2010-08-20
forum: Multimedia Software
---

### Post by niceguy123 on 2010-08-20
I am using a sony viao VGN-FW250j with Ubuntu 9.10   In an older Ubuntu the internal webcam had worked with Skype, although I never got the internal mic to work. 

Now after the upgrade to 9.10 the webcam is not showing a picture, although when I try a test in skype the little green light next to the camera goes on. 

Any suggestions?

Thanks,

BTW - I saw in other threads that some people said that their camera worked with cheese but not skype. So I installed cheese, but, my camera doesn't work there ether.

---

### Post by no2498 on 2010-08-20
put this in a terminal 1 at a time 

it may or may not help

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

---

### Post by niceguy123 on 2010-08-21
No,

Thanks for the help, but it didn't help. BTW - I am using 64 bit if that makes a difference.

---

### Post by no2498 on 2010-08-21
try this

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

### Post by niceguy123 on 2010-08-21
Thanks for the gstreamer-properties idea. I tried that and it worked on the test when I changed one to the other. But Skype and gmail video are still both not recognizing the webcam.

---

### Post by niceguy123 on 2010-08-22
Bump...

Webcam still not working in google, youtube, skype.

---

### Post by no2498 on 2010-08-22
did you retry cheese

---

### Post by niceguy123 on 2010-08-22
> **no2498 said:**
> did you retry cheese

Cheese is working, but not the others.

---

### Post by no2498 on 2010-08-22
retry these

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by niceguy123 on 2010-08-22
> **no2498 said:**
> retry these

LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

No change. Both of the above open skype, but in skype>options>video devices: No device found

---

### Post by no2498 on 2010-08-23
ok you have the cam working thats good 
now you need to ask a skype ?
you wont get any help on/in this 1

---

