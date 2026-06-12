---
title: "how to install &quot;listen&quot;"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by syxbit on 2006-06-10
i've read a lot about a program "listen" that compares to amarok, but i don't know how to install it.
i've tried searching for it, but can't find it
care to help ?

---

### Post by Jussi Kukkonen on 2006-06-10
[http://listengnome.free.fr/](http://listengnome.free.fr/)

There is a repo for dapper at [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/)

EDIT: just in case I was a little blunt: You should probably install a .deb first and see if you like it (after making sure you trust the guys who distribute it of course -- downloading stuff from the net does have its dangers...). If you do  like it, add the repository to your sources.list, so you'll get the updates.

---

### Post by BitTorrentBuddha on 2006-06-10
```
sudo nano /etc/apt/sources.list
```
(You can replace nano with your preferred text editer) Add "deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./" without quotes to the bottom of that file, save it and then run ```
sudo apt-get update
sudo aptitude install listen
``` That should do it, if you want to do it an easier way, the automatix script will install it for you. 
Good Luck :)

EDIT: Jussi beat me to it, I'll leave my instructions in case somebody needs them though.

---

### Post by syxbit on 2006-06-10
wow, thanks guys
i like the player, but it really doesn't seem much different from rythmnbox
i have a question
how did you know the repo, and  why did you put a "./" at the end (it worked great, but i'm just curious)

---

### Post by BitTorrentBuddha on 2006-06-13
The repo was actually automatically added for me while running the automatix script. I figured since you were only looking for listen, I wouldn't tell you to download and run the entire script.

---

