---
title: "[SOLVED] Desktop looks like garbage after selecting correct driver"
date: 2008-07-13
forum: Multimedia Software
---

### Post by Jordanwb on 2008-07-13
My laptop has a S3 Savage4 video chip with 4MB of video RAM. In KDE I changed the driver from S3 Savage (Generic, sw_cursor) to S3 Savage4 (which it should be), and now the highest resolution I can have is 640 X 480. I changed it back to the Generic one and the highest resolution is 640X480.

[Solved] I was able to "fix" it by restoring the /etc/X11/xorg.conf file that was in a backup that I made.

---

