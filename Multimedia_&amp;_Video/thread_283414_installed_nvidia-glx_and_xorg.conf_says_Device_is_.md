---
title: "installed nvidia-glx and xorg.conf says Device is &quot;ATI...&quot;"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by 504yaj on 2006-10-24
I have a problem with nvidia-glx. I just installed dapper drake, installed the latest nvidia-glx, then enabled it (sudo nvidia-glx-config enable)

edited xorg.conf and saw "ATI blah blah" on the device name, what gives? I have a PCI-E GeForce 6600GT, never new ATI produced these mofos too

I tried to restart without editing it and Xserver wont start.

---

### Post by CatKiller on 2006-10-24
```
sudo dpkg-reconfigure xserver-xorg
``` may help you get X server going again.

---

### Post by tseliot on 2006-10-24
Try this:
```
sudo nvidia-xconfig
```

it's all explained in Method 1 of my guide:
[Guide for Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

[Guide for Edgy]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy")

---

