---
title: "ManDVD: ERROR during ffmpeg execution!"
date: 2008-06-19
forum: Multimedia Software
---

### Post by MrSootentai on 2008-06-19
I keep getting this error in ManDVD whenever I create the picture slideshow. I've tried editing the dvd-slideshow to use 'ac3=0' instead of the 'ac3=1' like I read from a blog it hasn't proven to help. I have no idea what to do now, and I need help ASAP on this. Can anyone suggest anything??
I've attached a copy of the log file.

---

### Post by dhughes on 2008-06-20
I had the same problem and this suggestion worked for me.


[http://ubuntuforums.org/showthread.php?t=788047](http://ubuntuforums.org/showthread.php?t=788047)

[quote="gerben1"] Re: dvdslideshow problem
I found out how to solve it in the end, it is in another thread, but anyways to get dvdslideshow working, just run these 2 commands in the console:
Code:

sudo apt-get install libsox-fmt-all
sudo sed -i 's/-ab 192/-ab 192k/g' /usr/bin/dvd-slideshow

The first command will install all sox libraries, it is only about 1 Mb in total, and the second command does the necessary text replacement in the dvd-slideshow script.

see this thread:
[http://ubuntuforums.org/showthread.php?t=788085](http://ubuntuforums.org/showthread.php?t=788085)[/quote]

---

### Post by MrSootentai on 2008-06-20
Thank you so much!
You just saved me from a load of trouble.
=]

---

