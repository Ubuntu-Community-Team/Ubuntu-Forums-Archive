---
title: "Resolution Problem"
date: 2006-09-12
forum: Multimedia &amp; Video
---

### Post by xkenshin on 2006-09-12
I quite new to this Ubuntu.
I manage to installed Ubuntu successfully.
The problem is, I'm using 17" monitor and set the resolution to 1280 , then i want to change it to 1024. I manage to change using the preference-> resolution .. when i click ok.. screen flickering.. and i've been kicked to login screen and the resolution still not changed. Could somebody help me?

---

### Post by Slychilde on 2006-09-12
You can try this.  Make a backup of your xorg.conf file first.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then run these commands and follow the prompts.  When it asks for resolution uncheck (by using spacebar) all but the resolution you want.

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

Hopefully, that *should* work for you.  If it doesn't you will have to restore your old xorg.conf to get your desktop back, most likely.

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Cheers.  Hopefully that helps!

---

