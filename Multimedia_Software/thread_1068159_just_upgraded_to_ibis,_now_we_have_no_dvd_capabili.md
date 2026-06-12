---
title: "just upgraded to ibis, now we have no dvd capabilities"
date: 2009-02-12
forum: Multimedia Software
---

### Post by dcperkins on 2009-02-12
Hello- both my husband and I just upgraded to Ibis on our laptops, and now we suddenly have no dvd players capabilities.  We have vlc and gnome movie player, and we have tried several different dvds, and it isnt working.
Help?

---

### Post by mttman on 2009-02-12
hello,

I believe the problem is that you don't have libdvdcss2 installed,
try ```
 sudo apt-get install libdvdcss2 
``` it will probably have a bunch of dependent packages associated with it. if it gives you an error message about not finding the package you need to make the multiverse repo's available. check this guide if you have more problems

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux]("http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux")

Hope this works

<Mttman>

---

### Post by dcperkins on 2009-02-12
Ok- i tried to enter that into the terminal and it said it is "not available but is reffered to  by another package.  this may mean that the package is missing, has been obsoleted or may only be available by another source"
So then i tried to look for it in synaptyk, and it wasnt there either. the closest we found was something like libdvdread3, which it says is already installed.

---

### Post by mttman on 2009-02-12
libdvdcss2 is an encryption library for dvds with css (Content Scramble System) on it. i'm pretty sure you can get it from Ultimatix (google this program) but i've always had problems with that one. check the link i gave in my last post, i believe it's a step by step instruction on getting dvd's to play in Ubuntu

<Mttman>

---

### Post by dcperkins on 2009-02-12
thanks.
its strange that all that got wiped when i upgraded.  But it works now. thanks.

---

### Post by UbuntuNerd on 2009-02-12
install ubuntu restricted extras in a terminal type this:
```
sudo apt-get install ubuntu-restricted-extras
```

---

