---
title: "Gray Flash problem"
date: 2009-11-24
forum: Multimedia Software
---

### Post by grkuntzmd on 2009-11-24
I am running Kubuntu 9.10 x64, but this problem also occurred in 9.04 (Ubuntu - Gnome) and 8.10 (x64).

I installed Adobe Flash from the restricted repositories.

When I start firefox, Flash works. If I use firefox for a while (couple of hours), Flash stops working, showing only a gray area and 'Done' on the firefox status bar. Restarting firefox fixes the problem for a while, then it recurs.

While Flash is working, right-clicking on the Flash area shows the usual popup-menu, but after is stops working, right-clicking has no effect.

Any ideas?

Thanks, Ralph

---

### Post by shaviro on 2009-11-24
I have the same problem with Flash in Firefox, running Ubuntu 9.10

---

### Post by grkuntzmd on 2009-11-24
Are you running x86 or x64?

---

### Post by HappyFeet on 2009-11-24
First, uninstall flash. Then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then get the [64bit flash]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") file.

Right click it and **extract here**. You will be left with **libflashplayer.so** file. Put the libflashplayer.so file in your home folder.

Then do:```
sudo cp /home/your_user_name/libflashplayer.so /usr/lib64/mozilla/plugins
```

Make sure to put *your name* where I wrote your_user_name.

Restart firefox if open.

You see, you were using the 32bit flash file which does not always work well in 64bit ubuntu.

I do this, and it works every time. Let us know how it goes.

---

### Post by grkuntzmd on 2009-11-24
I installed the Adobe Flash player from the repositories. I believe it IS the 64-bit version already (in 9.10). How can I tell whether it is the x86 or x64 version?

---

### Post by HappyFeet on 2009-11-24
> **grkuntzmd said:**
> I installed the Adobe Flash player from the repositories. I believe it IS the 64-bit version already (in 9.10). How can I tell whether it is the x86 or x64 version?

If you followed my instructions, you would have working flash right now. The flash from the repos is 32bit, which does not work well with 64bit ubuntu.

---

### Post by grkuntzmd on 2009-12-08
The suggestion to use the latest x64 Flash did NOT work. I still get the gray screens.

---

