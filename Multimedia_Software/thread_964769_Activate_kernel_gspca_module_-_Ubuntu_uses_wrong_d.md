---
title: "Activate kernel gspca module - Ubuntu uses wrong driver"
date: 2008-10-31
forum: Multimedia Software
---

### Post by Petroy on 2008-10-31
Hi,

I have the webcam WB-3250p by Trust which is said to be working with the gspca driver. gspca is included in the 2.6.27 kernel shipped with Intrepid.

Unfortunately, Ubuntu uses the sn9c102 driver for the camera instead. I have now blacklisted the sn9c102 module via editing /etc/modprobe.d/blacklist .

How can I now make Ubuntu use the gspca kernel driver?


Regards,
Petroy

---

