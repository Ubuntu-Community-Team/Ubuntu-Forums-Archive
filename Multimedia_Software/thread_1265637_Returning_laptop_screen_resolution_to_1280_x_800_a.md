---
title: "Returning laptop screen resolution to 1280 x 800 after use of external monitor"
date: 2009-09-13
forum: Multimedia Software
---

### Post by halbuquerque on 2009-09-13
Hi,

I had plugged an external LCD to my laptop running Ubuntu Jaunty Jackalope (9.04) and the automatic configuration of the laptop display was set to 1024 x 768. After unplugging the LCD, I couldn't get back to the original laptop config of 1280 x 800.

I thought this might be useful for other beginners who might have the same problem as I did, so here's what's worked for me:

1. Edited the xorg.conf file:
```
sudo gedit /etc/X11/xorg.conf
```2. Followed the instructions in the file and ran the command below to restore the defaults:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```3. Accessed "System > Preferences > Display" and, voilá, the 1280 x 800 option was back as one of the options. Selected it and was done.

Best regards to all,

Henrique

---

