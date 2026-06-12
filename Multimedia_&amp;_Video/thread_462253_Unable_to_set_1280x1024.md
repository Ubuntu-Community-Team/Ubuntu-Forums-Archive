---
title: "Unable to set 1280x1024"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by solarwind on 2007-06-02
Hey all, I have an HP A4331A CRT monitor and the maximum resolution that the screen resolution app will let me set is 1024x768. I have the nVidia drivers for my card but I am unable to set 1280x1024. Can anybody help me?

---

### Post by crispy_420 on 2007-06-02
Try posting your xorg.conf, that resolution may not be there and you may have to reconfigure your nvidia drivers.

---

### Post by Nythain on 2007-06-02
if your nvidia drivers are installed and set up correctly you could just type
gksudo nvidia-settings
make the changes there and save them
or you could
sudo dpkg-reconfigure -phigh xserver-xorg
and set it that way, or you could 
gksudo gedit /etc/X11/xorg.conf
and add the resolutions you want that way

---

