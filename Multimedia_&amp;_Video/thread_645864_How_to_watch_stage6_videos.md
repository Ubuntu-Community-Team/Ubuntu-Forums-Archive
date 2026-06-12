---
title: "How to watch stage6 videos?"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by boast on 2007-12-20
I've googled and searched, but I can not find it.

There is some config file which you do 'divx=1' and it works. I just reinstalled so I forgot what it was.

It is none of that firefox plugin stuff, vlc, or any of that.

---

### Post by yabbadabbadont on 2007-12-20
[http://ubuntuforums.org/showthread.php?t=540412&highlight=howto+stage6](http://ubuntuforums.org/showthread.php?t=540412&highlight=howto+stage6)

---

### Post by gb5uqx on 2007-12-20
The only thing i can think of like that is the mplayer mozilla plugin config which either has or needs a line like that saying **enable-divx=1** or similar.

```
sudo gedit /etc/mplayerplug-in.conf
```

I found simply installing the divx codec for linux debian from divx.com was enough to get my default totem player working just fine in FF.

if you want to use mplayer plugin and don't actually have it just install with

```
sudo apt-get install mozilla-mplayer
```

Then create the necessary symlinks to handle divx at stage6 with

```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so /usr/lib/firefox/plugins/mplayerplug-in-dvx.so
```

```
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt /usr/lib/firefox/plugins/mplayerplug-in-dvx.xpt
```

If buffering is a problem just increase the cache size in mplayerplug-in.conf

You may need to disable any other plugin you may have such as totem or vlc.

---

### Post by boast on 2007-12-20
I tried that guide, but didn't work for me.

---

### Post by yabbadabbadont on 2007-12-20
It just worked for me.  I couldn't view the videos, followed the guide instructions for Feisty, now I can view them...  :?

Edit: You have to be sure to remove all other video plugins, like vlc's and totem's.

---

### Post by boast on 2007-12-20
oh, I guess totem-mozilla reinstalled itself.

nm.

---

