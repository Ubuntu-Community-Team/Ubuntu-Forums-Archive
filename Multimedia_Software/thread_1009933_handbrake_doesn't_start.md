---
title: "handbrake doesn't start"
date: 2008-12-13
forum: Multimedia Software
---

### Post by uberdonkey5 on 2008-12-13
Want to be able to edit or convert AVCHD to editable format (I use avidemux usually)

Using hardy. Have Panasonic HDC-SD9 and only produces high definition video (AVCHD). Software with camera worse than rubbish.

Tried this to convert mts file (AVCHD) to avi file
[http://wesleybailey.com/articles/m2tstoavi-avchd](http://wesleybailey.com/articles/m2tstoavi-avchd)
It works but video slows down putting sound progressively more out of sync with video.

Handbrake is suggested.
[http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)
seems to be a fantastic package, but I have tried installing it twice (with deb installer). All goes well with icon on menu etc, but when I click on icon it doesn't start. It has absolutely no effect.

Help with problem with handbrake, or suggestion of better user friendly conversion package (want to retain high quality video if possible) appreciated.

---

### Post by pseudonym on 2008-12-13
Unfortunately the Handbrake website doesn't include all the files you need to install the package. I got mine directly from the Ubuntu developer who packaged it by adding his repo to my sources.list -

deb [http://ppa.launchpad.net/handbrake-ubuntu/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ubuntu) intrepid main

I then uninstalled the single handbrake .deb I got from the project website and installed the program via apt-get instead.

I can't say I was impressed with the quality, though. Many people rave about Handbrake but I get better quality xvid encoding using [dvd::rip]("http://www.exit1.org/dvdrip/"). This program is more configurable than Handbrake as well. I don't know how well it would handle your stuff, though. But, like in anything, YMMV.

---

### Post by uberdonkey5 on 2008-12-15
thanks pseudo,
To be honest, there are so many options, most of which DON'T work. Considering that HD is better quality, I'd like to retain quality. I've watched it on an HD TV direct from my vid cam, and the quality is great. Unfortunately I think I have become very fed up with trying to use linux with HD video. Tonight I will try it with Blender (I tried it with cinelerra and couldn't get it to work, though noticed something very complicated in the cinelerra manual which may work, but I would rather not risk wasting any more time).

If I can't get it to work unfortunately I am going to buy Pinnacle Studo 11 Plus for Windows. Just frustrating because my windows system (dual boot) runs slower and is buggy.

ub5

---

