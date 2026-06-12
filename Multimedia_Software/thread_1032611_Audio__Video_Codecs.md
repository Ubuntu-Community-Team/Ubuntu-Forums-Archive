---
title: "Audio / Video Codecs"
date: 2009-01-06
forum: Multimedia Software
---

### Post by doggpound on 2009-01-06
Hi Everyone,

Im really new to the whole Linux environment, I recently got a copy of UBUNTU Version 8.04. Now here is the problem, I have installed it off the CD and everything seem fine, its just that i have no software that can play audio or video files. Another problem is that i do not have internet at home (only at work), so if someone could tell me how i could download the appropriate packages from work and then bring it home and install it I would really appreciate it. I want an winamp equivalent and mplayer.

Plese help.

---

### Post by SuperSonic4 on 2009-01-06
I believe the code is ```
sudo apt-get install -d *package*
``` and for packages you will want the **medibuntu repos**, **ubuntu-restricted-extras** and **xmms** (xmms is a winamp style music player)

---

### Post by markbuntu on 2009-01-06
This post here will help you get your sound set up properly with codecs etc

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by doggpound on 2009-01-07
So what you are saying is by typing the command:
sudo apt-get install -d *package* 

will this work if i do not have an internet connection, so what you are saying is that these packages are installed with the UBUNTU 8.04 CD and i just have to type this in?

---

### Post by anilcr on 2009-01-07
no ```
 sudo apt-get install -d [package] 
``` downloads the package from the Internet ( or CD if the packages are available, in your case its not ). **You can download it at work and install it at home**.
Except I don't know where the packages are stored.

---

### Post by anilcr on 2009-01-07
ok did some research, they're stored in /var/cache/apt/archives

---

### Post by doggpound on 2009-01-07
I checked in /var/cache/apt/archives and there are no packages there. How do i get these packages and install them? Please help. All I want to do is watch videos and play mp3s. 

Thanks

---

### Post by anilcr on 2009-01-07
no you need to use the command above to download them. once you download them you can get it from work to your place. 
Or if you have a friend who has access to Internet and uses ubuntu you can get the packages from him/her

---

### Post by doggpound on 2009-01-08
Oh Ok. Is there no other way I can download it manually?

---

### Post by anilcr on 2009-01-08
see if you can find anything here:
[http://ubuntuforums.org/showthread.php?t=572819&highlight=apt-move+iso&page=2](http://ubuntuforums.org/showthread.php?t=572819&highlight=apt-move+iso&page=2)

---

