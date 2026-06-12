---
title: "How to change video drivers from command line"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by LeToastaire on 2007-12-24
Hey

I was trying to get an external secondary monitor to run parallel with my laptop and realized I couldn't do it with my current situation.  I went into the administrator toolbar and changed what video driver I was supported by.  When I restarted my computer to affect the changes, it wasn't able to render any visuals.  I was thrust into the command line and I have no idea how to revert to my old driver without reinstalling Ubuntu.  

So I guess my question is my thread title: How do I change my driver settings back to what they were from the command line?  It was something like intel experimental I don't know, whatever the default was for my Inspiron. 

Thank you.

---

### Post by nick_h on 2007-12-24
You can reconfigure your video by typing:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
In future, when you have a working system, make a backup of your /etc/X11/xorg.conf file so that you can restore it if necessary.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

