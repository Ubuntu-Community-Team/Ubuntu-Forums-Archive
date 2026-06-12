---
title: "gstreamer &amp; webcam"
date: 2010-04-03
forum: Multimedia Software
---

### Post by hamid_m on 2010-04-03
hi , I want save video and sound from webcam and save them in avi format  , I use this command but not work , how can fix it

gst-launch v4l2src device=/dev/video0 ! queue ! videorate ! xvidenc !queue !alsasrc device=hw:0,0  ! audioconvert  ! queue ! avimux  ! filesink location=test.avi

---

