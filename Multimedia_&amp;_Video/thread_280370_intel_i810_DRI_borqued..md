---
title: "intel i810 DRI borqued."
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by mking213 on 2006-10-19
I tried to install the .deb from intel's website for the d915gag onboard video and it broke DRI. I tried to uninstall the package to no avail! HELP!

mike@malakai:~$ glxinfo |grep rend
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

mike@malakai:~$ cat /etc/X11/xorg.conf |grep Driver
        Driver          "kbd"
        Driver          "mouse"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
        Driver          "i810"

---

### Post by mking213 on 2006-10-19
I fixed it, i had to reinstall linux-686 and restricted modules.

---

### Post by almahtar on 2006-10-20
Thanks for posting your fix. It saved me some time.

---

