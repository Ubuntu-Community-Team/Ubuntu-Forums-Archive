---
title: "Every video is blue"
date: 2011-05-15
forum: Multimedia Software
---

### Post by NoMercyZL on 2011-05-15
Hi! I am new to Ubuntu.
Every time I play a video it's blue. I've tested several video formats and several players but it's the same problem. Even in sype the problem exist. Every thing else is normal and even youtube videos show proberly. Here is an example: [IMG]http://i51.tinypic.com/30ufii8.png[/IMG]

Can you please help me:)

---

### Post by sikander3786 on 2011-05-15
That is something new to me :-)

Which graphics card is there? Which version of graphics drivers is installed (if any). And which version of Ubuntu is this?

From Applications > Accessories > Terminal, you can post the output of these command.

```
lspci | grep VGA
lsb_release -a
```

---

### Post by lindsay7 on 2011-05-15
it is a problem with codecs

see this for some info, depending on your version of unbunto, you may need to install the correct stuff.

[http://yopensource.com/fr/news/ubuntu-latest-news/1790-install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-1004-lucid-lynx](http://yopensource.com/fr/news/ubuntu-latest-news/1790-install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-1004-lucid-lynx)

---

### Post by NoMercyZL on 2011-05-15
lindsay7 the codec you posted didn't work.:(
Here are my information:

01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)


No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

---

### Post by NoMercyZL on 2011-05-15
Now I installed Gnome Mplayer and the videos work fine but they still don't work with other players:(
Could you please help me:D

---

### Post by lindsay7 on 2011-05-15
What version of Ubuntu are you running?

---

### Post by NoMercyZL on 2011-05-15
11.04

---

### Post by lindsay7 on 2011-05-15
Maybe this will help,

[http://ubuntu-install.blogspot.com/2011/05/ubuntu-114-installation-tips.html](http://ubuntu-install.blogspot.com/2011/05/ubuntu-114-installation-tips.html)

---

### Post by wojox on 2011-05-15
[Fix blue tinted video in Ubuntu]("http://www.wiredrevolution.com/ubuntu/fix-blue-tinted-video-in-ubuntu")

---

### Post by NoMercyZL on 2011-05-15
Thanks wojox! it worked.:) And thank everyone who tried to help me.

---

