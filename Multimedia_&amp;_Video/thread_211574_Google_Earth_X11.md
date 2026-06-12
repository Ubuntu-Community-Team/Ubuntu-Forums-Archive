---
title: "Google Earth X11"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by matt91 on 2006-07-08
i have tried to install google earth in ubuntu today but all i get is this:
> 
root@ubuntu-pc2:/home/matt# ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.1660..................................................................
You don't see to be running an X server (no DISPLAY set).
Google Earth and its installer both require X11.
Aborting...
root@ubuntu-pc2:/home/matt#

ubuntu seems to have X11/Xorg installed although i dont realy know anything about it. Does anybody know how to fix this?

thanks, Matt

---

### Post by SoftGround on 2006-07-08
try 
```
export DISPLAY=":0.0"
```
before running it (this sets the DISPLAY environment variable to the local screen.
Then see if you get the same error message.

---

### Post by whatever on 2006-07-08
why are you trying to run it as root? [-X

---

### Post by habys on 2006-07-10
this might have something to do with his methodology:
from [http://ubuntuguide.org/wiki/Dapper:](http://ubuntuguide.org/wiki/Dapper:)


>  How to install Google Earth

    * Read #General Notes 

wget -c [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sudo sh GoogleEarthLinux.bin

    * Leave /usr/local/google-earth as the installation path
    * After installation click Exit. If you instead chose to run the application, read the Note below. 

sudo cp /usr/local/google-earth/googleearth.desktop /usr/share/applications/

    * Applications -> Internet -> Google Earth 

    * Note: If you run Google Earth for the first time from the installer, it will require root privileges to run the next time. To fix that: 

sudo chmod 777 -R ~/.googleearth 

---

