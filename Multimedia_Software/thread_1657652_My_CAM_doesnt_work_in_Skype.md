---
title: "My CAM doesnt work in Skype"
date: 2011-01-01
forum: Multimedia Software
---

### Post by rainblue72 on 2011-01-01
Hello Guys. My webcam does not work in Skype while it works fine with Cheese. I found following path in forums and tried it:
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so /usr/bin/skype

In Skype I selected Options/Video Devices/ Test

The webcam light is on but I see only blank screen. In Terminal, it gives following error message:

X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 

Any idea how to fix it?

I use Ubuntu 10.04
Skype 2.1.0.81

Thanks!

---

### Post by lidex on 2011-01-01
Have a look here:
[https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting)

More:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by rainblue72 on 2011-01-02
> **lidex said:**
> Have a look here:
[https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting)

More:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Thanks a lot!! It fixed it perfectly!!

---

