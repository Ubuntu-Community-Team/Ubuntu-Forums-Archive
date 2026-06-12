---
title: "Sound from Banshee no sound from Youtube/Vimeo..."
date: 2010-06-21
forum: Multimedia Software
---

### Post by Rhetoric Camel on 2010-06-21
Hello I have installed Ubuntu 10.04 yesterday on my computer. After install I played music and videos from youtube and vimeo and facebook just fine with no issues. For some reason today when I try to play videos in firefox I'm not getting any sound but still getting sound from Banshee when I play music.

I've tried 
```
sudo apt-get install libflashsupport
```
which seems to work for others, and I get this after hitting enter
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  flashplugin-nonfree-extrasound
E: Package libflashsupport has no installation candidate

```

I have tried disabling Tools>Add ons>Ubuntu Firefox Modifications after reading that it has helped some others.

I'm not seeing much else around and have no idea where to start. I tried upgrading alsa last night using the directions from this page: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
After that things were still working, but today they're not. Don't know if after that update they didn't take affect until I restarted. 

Other than that, there is nothing else I have done that could have caused this issue. Any help would be great!

---

### Post by Rhetoric Camel on 2010-06-21
Ok so I found a post on the forums that mention to type this into the terminal and then reboot

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd
```

I did it and it seems to work now. Anyone know why this happened and why this fixed it? It's nice getting a fix but I'd still like to know what could have caused this issue.

---

