---
title: "Webcam does not work on Skype"
date: 2011-04-04
forum: Multimedia Software
---

### Post by CaKiwi on 2011-04-04
I have a WinBook webcam model DC-6120 which works fine on on my desktop in both Cheese and Skype. However, on my Compaq CQ60 laptop it works in Cheese but not in Skype. I am using Ubuntu 10.10 and Skype 2.1.0.81 on both systems

Any help greatly appreciated.

---

### Post by MichaelLerch on 2011-04-04
I am having a similar issue however the webcam works but the built-in mic doesn't. It's a Microsoft VX-5000 (or similar) model. I don't know the exact model number because I only Googled the image.

As far as OPs issue, have you checked to see if the device is installed? If you need help doing that, let me know. I'm not on my desktop at the moment (which has Windows 7 and Ubuntu 10.10 dual boot).

---

### Post by CaKiwi on 2011-04-04
Thanks for the reply, MichaelLerch. 

How do I tell if it's installed? Also, if it's not installed, why would it work with cheese.

---

### Post by CaKiwi on 2011-04-05
Does anyone have any thoughts on this?

---

### Post by CaKiwi on 2011-04-05
I fixed this problem by replacing the command to start Skype with

```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```

I found this at 

[https://help.ubuntu.com/community/Webcam/Troubleshooting](https://help.ubuntu.com/community/Webcam/Troubleshooting)

---

