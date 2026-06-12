---
title: "Adobe Flash amd64 Fix!!!"
date: 2010-02-09
forum: Multimedia Software
---

### Post by Biospower5000 on 2010-02-09
[SIZE=2][FONT=Arial]Hello all!, if somone needed help to install flash player on 64bit ubuntu mozilla firefox here comes the fix:

Remove *_ALL FLASH PLAYER, GNASH SWFDEC, etc_* players next go to a site showing flash (not youtube) let firefox search for plugins and select: adobe flash player(installer)

Hope it helpsXD!
[/FONT][/SIZE]

---

### Post by HappyFeet on 2010-02-09
> **Biospower5000 said:**
> [SIZE=2][FONT=Arial]Hello all!, if somone needed help to install flash player on 64bit ubuntu mozilla firefox here comes the fix:

Remove *_ALL FLASH PLAYER, GNASH SWFDEC, etc_* players next go to a site showing flash (not youtube) let firefox search for plugins and select: adobe flash player(installer)

Hope it helpsXD!
[/FONT][/SIZE]

That's an *OK* solution, but you would just be using the 32bit flash plugin with a wrapper. Better to use the 64bit plugin.

First, uninstall the flash you have. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

---

### Post by Maheriano on 2010-02-09
Ya, there are native 64 bit players, why would you use 32 bit?

---

