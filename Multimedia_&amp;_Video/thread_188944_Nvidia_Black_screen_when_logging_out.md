---
title: "Nvidia: Black screen when logging out"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by M3D on 2006-06-04
Hi everybody! I'm a complete newbie and today installed linux for the first time.
Ubuntu 6.06 is working properly, as the Nvidia driver do, except when logging out or restarting the Xserver (I learnend some fancy words today!). In both cases I get black screens, but the computer is still alive cause I hear the sounds of the login screen.

If I change xorg.conf setting from "nvidia" back to "nv" the problem is solved, but of course, I don't have 3D acceleration.

I have a Geforce FX Go5700 and I'm running 87.62 drivers.

Any help will be inmensely apreciated!!!

---

### Post by M3D on 2006-06-04
Thanks to **tseliot** and for his answer in this post:
[http://www.ubuntuforums.org/showpost.php?p=1092406&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1092406&postcount=3)

This fixed my problem, which I supose was the same as **jojopaderes**.

---

### Post by tonyr on 2006-06-04
If you haven't already, look at  [Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")
and use **Method 1**.  Some people have had to make an additional change to
**/etc/X11/xorg.conf**  by adding the line
```

Option    "NvAGP" "1"

```
in the section where you changed "nvidia" to "nv".  One person had to use "0" instead
of "1".

EDIT:  Sometimes you have to remove the **splash** option from the **kernel**
line in **/boot/grub/menu.lst**.

---

