---
title: "I thought I turned off the screen saver..."
date: 2008-05-09
forum: Mythbuntu
---

### Post by Caps18 on 2008-05-09
Is there a way to prevent the screen from going black after 10 minutes of idle time?  I know that I turned off the screen saver in the settings, but it still happens.

Is there a setting in mythtv that is causing this?

---

### Post by girishv on 2008-05-09
May be the gnome power manager is blanking the screen after 10 minutes. you can change these setting using
gnome-power-preferences

Girish

---

### Post by sgunther on 2008-05-09
In addition to disabling after 10 minutes in the preferences for the screensaver do the following;

```

sudo nano /etc/X11/xorg.conf
```

Put your password in when it asks for it.

Go to the bottom and add;

```
Section "ServerFlags"
 Option "blank time" "0"
 Option "standby time" "0"
 Option "suspend time" "0"
 Option "off time" "0"
 Option "screen blank" "0"
EndSection
```

Then Ctrl-X to exit

Answer Yes to "Save modified buffer (ANSWERING "No" WILL DESTROY CHANGES) ?"

And press enter to save to the file name you started with.

When you are done you need to restart gdm;

```
sudo /etc/init.d/gdm restart
```

Or you can just reboot.

```
sudo reboot
```

---

### Post by Caps18 on 2008-05-09
It looks like adding that to the xorg.conf file solved it. 

Thanks.

---

### Post by Trollslayer on 2008-06-16
Works for me as well (Mythbuntu 8.04 - MythTV 0.21), thanks.

---

### Post by williammanda on 2009-09-09
I have a few questions concerning this fix....
1. Does this totally disable the screen saver?
2. If not, it only for mythmusic?
3. What I can see it totally disabled the screen saver. What if you only want this option in mythmusic?
Thanks

---

