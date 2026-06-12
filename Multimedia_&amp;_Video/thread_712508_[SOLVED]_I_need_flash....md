---
title: "[SOLVED] I need flash..."
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by paragrini on 2008-03-01
I am VERY new to ubuntu... I mean I installed it no more than an hour ago... and I can't figure anything out.. but the one thing I do need is flash... I tryed installing it from the website but it told me that the archiver didn't support the format... I need help... cause I really need flash... please help...
Thank you
Para

---

### Post by justin whitaker on 2008-03-01
> **paragrini said:**
> I am VERY new to ubuntu... I mean I installed it no more than an hour ago... and I can't figure anything out.. but the one thing I do need is flash... I tryed installing it from the website but it told me that the archiver didn't support the format... I need help... cause I really need flash... please help...
Thank you
Para

Flash the program, or the pugin?

The plugin is part of the Ubuntu-restricted-extras package, as well as a standalone in Add/Remove, or Synaptic. 

For Flash, you will need an earlier version, and WINE. :)

---

### Post by paragrini on 2008-03-01
Ok... So I got synaptic and the download for linux of flash... but I don't know were to go from here... I really suck at this... but I think I'm making headway in my first hour... lol... please help if you can..
thank you
Para

---

### Post by Sam Lars on 2008-03-01
What package did you install through Synaptic?

---

### Post by paragrini on 2008-03-01
Umm.... help more please...

---

### Post by aysiu on 2008-03-01
Try this:
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

I'm not sure if *flashplugin-nonfree* is working right now.

---

### Post by Sam Lars on 2008-03-01
From this thread:
[http://ubuntuforums.org/showthread.php?t=290785](http://ubuntuforums.org/showthread.php?t=290785)

```
cd ~
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar xvfz install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
sudo ./flashplayer-installer
```

---

