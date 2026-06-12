---
title: "Flash not working on specific site"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by timzak on 2007-09-20
[http://www.joelrosenberg.com/](http://www.joelrosenberg.com/)

The site above tells me to install Flash Player 8.  Could it be that it supports version 8 but not 9?  I have the latest version of Flash installed, but I did notice in about:plugins that there are two Flash sections.  At the top of the about:plugins page is version 9.0 r48, and the very last entry at the bottom of the page is version 9.0 r31.  Should there be two entries, and could this be why I'm having problems viewing this page?  I tried viewing the offending page on a Windows machine and it displayed properly.

---

### Post by timzak on 2007-09-21
*bump*

I've since found another site that tells me I'm not using the latest version of Flash and to upgrade it.  It links me to the Adobe Flash download page for 9.0.48...which according to about:plugins, I already have installed!  Any ideas?

---

### Post by RomeReactor on 2007-09-21
Hi. The site plays fine here with Flash 9.0 r48. Close Firefox and delete the XPTI file in the **.mozilla/firefox/********.default** folder that's located in your home folder. From the terminal (Applications->Accessories->Terminal):
```
rm ~/.mozilla/firefox/*.default/xpti.dat
```
Now open Firefox again and go to the site. Did you install Flash from two different sources (e.g., from Synaptic and then from the Adobe site, or viceversa)?

If that doesn't work, you could try removing the flash plugin you currently have and install it again. Close Firefox and run these commands in the terminal:
```
locate libflashplayer.so
```
If you only get this:
> /usr/lib/mozilla/plugins/libflashplayer.so
then run:
```
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
```
and
```
rm ~/.mozilla/firefox/*.default/xpti.dat
```
to remove the plugin and the XPTI file;
```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```
to get the most current flash version;
```
tar -xvvzf install_flash_player_9_linux.tar.gz
```
to extract the file;
```
cd install_flash_player_9_linux/
```
to go into the newly created folder; and
```
./flashplayer-installer
```
to install flash again.

Now open Firefox again and see if you still have the problem.

---

### Post by timzak on 2007-09-21
> **RomeReactor said:**
> Hi. The site plays fine here with Flash 9.0 r48. Close Firefox and delete the XPTI file in the **.mozilla/firefox/********.default** folder that's located in your home folder. From the terminal (Applications->Accessories->Terminal):
```
rm ~/.mozilla/firefox/*.default/xpti.dat
```
Now open Firefox again and go to the site. Did you install Flash from two different sources (e.g., from Synaptic and then from the Adobe site, or viceversa)?

If that doesn't work, you could try removing the flash plugin you currently have and install it again. Close Firefox and run these commands in the terminal:
```
locate libflashplayer.so
```
If you only get this:

then run:
```
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so
```
and
```
rm ~/.mozilla/firefox/*.default/xpti.dat
```
to remove the plugin and the XPTI file;
```
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```
to get the most current flash version;
```
tar -xvvzf install_flash_player_9_linux.tar.gz
```
to extract the file;
```
cd install_flash_player_9_linux/
```
to go into the newly created folder; and
```
./flashplayer-installer
```
to install flash again.

Now open Firefox again and see if you still have the problem.

Thank you for the detailed response.  As is almost always the case, the problem was operator error and not the OS.  I discovered that my problem was the NoScript Firefox extension.  Specifically, I needed to whitelist the website in NoScript.

Thank you so much for your time in helping me and I apologize for not catching the problem myself before posting.

Regards.

---

### Post by RomeReactor on 2007-09-21
No problem :popcorn:

---

