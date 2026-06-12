---
title: "Rollback Nvidia Drivers?"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by Tango_Down on 2006-11-07
What is the command to rollback to the Nvidia drivers your system used before an update? I acidently installed the xorg drivers when I should have ignored it and used the proprietary ones. They should just stop have update notifications for graphics card drivers, from the tone of the posts it causes more trouble than it fixes.

---

### Post by Paul41 on 2006-11-07
```
sudo dpkg-reconfigure xserver-xorg
```

If you are still able to start X and just want to change the driver you could also just edit the xorg.conf file.
```
gksudo gedit /etc/X11/xorg.conf
```

EDIT: This is for changing the driver. After reading your post again I think you are trying to go back to an older version of the dirver before the update. Sorry.

---

### Post by tseliot on 2006-11-07
> **Tango_Down said:**
> I acidently installed the xorg drivers when I should have ignored it and used the proprietary ones. They should just stop have update notifications for graphics card drivers, from the tone of the posts it causes more trouble than it fixes.

"nv" is the opensource driver while "nvidia" is the proprietary driver.

Which driver did you use and which one are you using now?

---

### Post by Tango_Down on 2006-11-12
I was using the proprietary driver. I likely switched to the open source one on accident. I am not sure, as I have no idea how to check with the X-server down, although with some searching I could probably find the command. I will try to install the most basic 'nv' driver and make my way from there. Thanks for the help. 
__
-Goodluck, Godspeed.

---

