---
title: "Webcam"
date: 2010-06-02
forum: Multimedia Software
---

### Post by cmani on 2010-06-02
My USB Webcam is listed as /dev/video0 when ls /dev/video*.
In skype, when i click "Test" button on video settings i am getting msg in log as  "libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?"
When i try with camorama i got error message "Could not connect to video device (/dev/video0).  Please check connection"

Pl. advise

---

### Post by no2498 on 2010-06-02
in/on 910 and up cheese webcam booth is/should be loaded
look in sound & video try the cam in it

you may need this for skype 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

put that in a terminal

---

### Post by cmani on 2010-06-02
Hi after enter the command as you suggested i am getting the error upon "test" in skype.

"libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?"

---

### Post by cmani on 2010-06-03
Hi,
Webcam is working with Cheese webcam booth, but not with skype?  Can anyone help me.

---

