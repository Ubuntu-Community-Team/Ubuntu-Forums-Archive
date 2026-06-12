---
title: "skype webcam issue"
date: 2011-05-25
forum: Multimedia Software
---

### Post by NeoReaper on 2011-05-25
so ive been having a strange problem since one of my updates and i finally realized what the issue is.  i have an old quickcam communicate stx and the problem im having is that skype trys to access the video input at 640x480 when it doesnt work right.  is there anyway i can force skype to only use 320x240 or is there a way i can limit the webcam driver to only use 320x240?

---

### Post by no2498 on 2011-05-26
you may try setting it in cheese
or in ekiga softphone
it may help skype

---

### Post by NeoReaper on 2011-05-26
unfortunately it appears that those settings are only applied to the application.  they dont seem to change any global settings which would assist by disabling skype from trying 640x480.  i tried setting up gstfakevideo in hopes that i can force it to use a specific resolution but oddly enough, in the latest version of ubuntu gstfakevideo does not compile.

---

### Post by no2498 on 2011-05-27
try this program guvcview
it has a lot of settings in it

open a terminal type dmesg click enter
see what size it sets


if still not working
in a terminal type gstreamer-properties click enter

click video you just try the test
try v4l and v4l2 
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

