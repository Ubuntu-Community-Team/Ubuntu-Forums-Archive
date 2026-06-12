---
title: "Greenish video after install of totem"
date: 2008-05-26
forum: Multimedia Software
---

### Post by Azyx on 2008-05-26
Hi.
I uninstall Totem in Gutsy for a while ago, because when I look at a movie totem change resolution to lower resolution in full screen, but don't change back afterward. Now after upgrade to Hardy Heron I think the mayby fix that problem. But now is there another problems. For VLC the sound drop out for a little while (less than a second) then the sound is loud or just some time. Very anoing.

Now I tried Totem-gstreamer again and now movies get a greenish tone and wrong color. After the installation of Totem-gstreamer even VLC show the movies in wrong colors :(

I follow the first steep in How-to [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
 but I was not able to install w32codecs. And get this message:

User@Computer:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
User@Computer:~$

now i wonder. how can I see a movie on Ubuntu? Why greenish color in the movie?

I have Ubuntu Hardy Heron upgraded from Gutsy.

---

### Post by mc4man on 2008-05-26
For tint issues read here, you should find solution
[http://ubuntuforums.org/showthread.php?p=5035483#post5035483](http://ubuntuforums.org/showthread.php?p=5035483#post5035483)
if for some reason they don't work run in terminal then restart
```
rm -rf ~/.gconf/apps/totem/
```

As far as w32codecs you may still have some gutsy sources that are preventing it from being installed or one of it's 2 dependencies from being updated
You should comment out any lines in /etc/apt/sources.list that refer to gutsy ```
gksudo gedit /etc/apt/sources.list
```  and then sudo apt-get update and try again (make sure you have medibuntu for hardy in your sources)    or run 
```
cat /etc/apt/sources.list
``` and post for some guidance

---

### Post by Azyx on 2008-05-27
Thanx mc4man :)

worked fine. :)

---

