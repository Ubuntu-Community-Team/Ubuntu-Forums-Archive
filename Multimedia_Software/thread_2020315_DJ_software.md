---
title: "DJ software"
date: 2012-07-08
forum: Multimedia Software
---

### Post by asai on 2012-07-08
Hi,

I will build a small disco with a stage where I want to play music and have the opportunity for karaoke. Is there software for Ubuntu that supports this?
Among other things I have heard of software that can remove lyrics from mp3 files.

---

### Post by dak0 on 2012-07-08
Hey there,

Dump, I need something similar too :)

---

### Post by shantiq on 2012-07-09
never used any of them myself but a few in the software centre

[ATTACH]220931[/ATTACH]

---

### Post by Whovian on 2012-07-12
I haven't tried this out yet myself but another way you could get some DJ would be to install wine an run the software known as [Virtual DJ]("http://download.cnet.com/Virtual-DJ/3000-18502_4-10212112.html?tag=contentMain;contentBody;1d") its a great software an the home edition is free.

```
sudo apt-get install wine
```

OR go to the software center an just type in wine an install.

Next if you want to have the latest version of wine type or paste this in:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

That will keep your wine distribution updated.

Afterwards you'll have to create the fake c drive which is done by the command winecfg

Installing windows applications:
```
wine whatprogramyouwant.exe
```

That is the basics of how it should work I'll leave some documentation to help you out more.

Documentation:
[http://www.winehq.org/download/ubuntu/](http://www.winehq.org/download/ubuntu/)
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

Good Luck!

---

