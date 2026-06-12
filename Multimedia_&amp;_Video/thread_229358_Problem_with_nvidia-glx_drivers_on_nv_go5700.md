---
title: "Problem with nvidia-glx drivers on nv go5700"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by Gaiachild on 2006-08-04
Hope someone can help me with this one:

Using a GF go5700 on an alienware laptop and everything works well with the standard nv drivers. However no matter what I do I cannot get it to work with the nvidia-glx drivers. As soon as gdm login screen tries to appear the screen is garbled. Tried with and without AGP, disabling EDID but nothing is working.

Attached are the xorg.conf and (abreviated) Xorg.log files.

Help :)

---

### Post by tseliot on 2006-08-04
Try point 7 of the Problems Section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by Gaiachild on 2006-08-04
Thanks for the reply,

Tried all the combinations in Section 7 now and still no go, however there was a slight change after editing the modprobe.d/options file in that gdm now loads and displays as a single line of pixels at the top of the screen where the rest of the screen is black. Over a few seconds the bottom slowly 'burns in' as patchy white areas.

---

### Post by tseliot on 2006-08-04
> **Gaiachild said:**
> Thanks for the reply,

Tried all the combinations in Section 7 now and still no go, however there was a slight change after editing the modprobe.d/options file in that gdm now loads and displays as a single line of pixels at the top of the screen where the rest of the screen is black. Over a few seconds the bottom slowly 'burns in' as patchy white areas.

remove the lines you put and ask for help here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

