---
title: "Install Problem With Nvidia Glx Driver"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by DonnieDarko on 2006-07-25
I get this message when I try type this into console **sudo nvidia-glx-config enable** and I get this error message

[B]Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.[/B]

I have installed the right drivers , but I still get that message can anyone help me? I have a EVGA Nvidia FX 5500 AGP.

---

### Post by tseliot on 2006-07-26
Try this:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "nvidia" driver. Press ENTER to the other questions

Next time, please use my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

