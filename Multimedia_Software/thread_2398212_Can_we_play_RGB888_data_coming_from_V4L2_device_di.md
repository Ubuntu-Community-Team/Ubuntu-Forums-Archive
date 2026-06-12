---
title: "Can we play RGB888 data coming from V4L2 device directly with VLC or anyother?"
date: 2018-08-09
forum: Multimedia Software
---

### Post by sagar143 on 2018-08-09
Hello,
I want to play RGB888 video frames in vlc, but this data doesn't have any header or any format. This data is coming from USB device which is a UVC or V4L2 device
can we play video directly? 

Thanks for help

---

### Post by ajgreeny on 2018-08-09
We need more info please.
What is this device; a webcam, and if so what make and model?
Show us the output of **lsusb** in terminal

Can you find the source USB device if you go to **VLC ->Media ->Open Capture Device -> Video drop-down box** or does that show an error of some kind?

Please use code tags for terminal output; if you're not sure about that see **Code Tags** in my signature for a "How-to".

---

