---
title: "Swapping ATI For Nvidia"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by Tumpster on 2007-09-04
Hey there, I just bought a new Nvidia card that I plan on putting as soon as it's arrives, now my question is this. How can I properly switch it over so Ubuntu sees the nvidia and unistall all the ATI drivers and get my nvidia card running well and everything kosher? I'd apprecaite any help at all!! :) Thanks!

Craig

---

### Post by taurus on 2007-09-04
You can edit /etc/X11/xorg.conf and replace whatever driver you are using right now to **vesa**.   Then, shutdown your computer and switch the video card.  Reboot and if everything, X, is running fine, then install the new nVidia driver for it.

Edit /etc/X11/xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```

Install nVidia driver:
```
sudo apt-get update
sudo apt-get install nvidia-glx-new nvidia-xconfig nvidia-settings
gksudo nvidia-xconfig
```

---

### Post by Tumpster on 2007-09-04
Thank you very much! I appreciate it!! :)

---

