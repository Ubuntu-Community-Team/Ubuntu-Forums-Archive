---
title: "flash stopped working after update to latest version"
date: 2009-12-11
forum: Multimedia Software
---

### Post by kayvee on 2009-12-11
I installed the recent update to flash player - the update was from Ubuntu Update Manager. Since then, I noticed that the controls on flash player do not always work (especially in Youtube). I am running Ubuntu Karmic 64-bit. Is this a known bug or something? Please help!

---

### Post by thogor on 2009-12-11
check out this thread it might help. [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1351156](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1351156) . Apparently it the plugin  version same effect in different versions of Linux. I downgraded, and it solved it for me.

---

### Post by HappyFeet on 2009-12-12
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

### Post by bigsmitty64 on 2009-12-12
> **HappyFeet said:**
> First, uninstall the flash you have. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

Right on! Thank you. I've been fighting with this all day! Worked perfectly!

---

### Post by kayvee on 2009-12-12
> **HappyFeet said:**
> First, uninstall the flash you have. Then do:
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

Thank you, it worked for me.

---

### Post by DutchSherpa on 2009-12-13
Does not work for me. The file libflashplayer.so is available in /usr/lib64/mozilla/plugins but Firefox does not seem to be aware of any flash player being installed.
I restarted and rebooted, but nothing happens. YouTube keeps on telling me I got JavaScript disabled (no, I have not) or I have got an old version of Flash player. 
What is missing in my setup? There is no flash player listed in the plugins or add-ons...

---

