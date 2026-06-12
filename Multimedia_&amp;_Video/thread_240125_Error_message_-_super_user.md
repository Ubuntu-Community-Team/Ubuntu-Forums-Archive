---
title: "Error message - super user"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by mmmpancakes on 2006-08-20
I'm trying to install a .run file installer from my desktop (to install a graphics driver) but I'm getting an error message that I Must be logged in as the super-user to run the installer. I only have one user account set up (mine!) and to the best of my knowledge I have all the priveleges. How do I log in as the super user?

---

### Post by mmmpancakes on 2006-08-20
bump

---

### Post by Ziox on 2006-08-20
> **mmmpancakes said:**
> I'm trying to install a .run file installer from my desktop (to install a graphics driver) but I'm getting an error message that I Must be logged in as the super-user to run the installer. I only have one user account set up (mine!) and to the best of my knowledge I have all the priveleges. How do I log in as the super user?

use this command:

sudo /(location of the file/.../(name of the run file)

sudo is the command to enter as super user

and that command, it'll prompt you for the password, which would be yours.  Be aware that you won't see "*" for password, there won't be anything at all...

---

### Post by tseliot on 2006-08-20
> **mmmpancakes said:**
> I'm trying to install a .run file installer from my desktop (to install a graphics driver) but I'm getting an error message that I Must be logged in as the super-user to run the installer. I only have one user account set up (mine!) and to the best of my knowledge I have all the priveleges. How do I log in as the super user?

If you're trying to install the Nvidia driver, please follow my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

or my Envy script:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

---

### Post by pollock.tar.gz on 2006-08-20
sudo = super user [ex. sudo ________]
sudo -s = root [to log in as root]

---

