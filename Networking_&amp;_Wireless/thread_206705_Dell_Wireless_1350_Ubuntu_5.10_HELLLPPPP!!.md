---
title: "Dell Wireless 1350 Ubuntu 5.10 HELLLPPPP!!"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by xzeginx on 2006-06-30
I am a linux newb. It just so happens that i have a linux class this quarter and i decited to go with Ubuntu 5.10 instead og Fedora 4. My problem is my Wifi. It is a Dell Wireless 1350. i pulled up directions on how to install NDIS wrapper and followed them to the "t". Does the driver that comes on the disk not work with ndis wrapper? When i pull up the driver info in ndisWrapper is says the the driver doesent work. Please help. I need this for school. I have a Dell Latitude 110L. If anyone can give me a step by step on how to get it working, that would be awsome...Feel free to E-mail me...xzeginx@gmail.com

---

### Post by rskovacs on 2006-07-01
ndiswrapper installation shouldn't be the problem, although if you are worried you could renistall it, but do it by installing the package ndisgtk, which I found much easier to install and use:

```
sudo apt-get install ndisgtk
```

I would then go to [this page]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") on the ndiswrapper wiki and try to find the driver that works for you.  In your case, it seems that #39, #40, or #45 under the letter D is probably what you are looking for.

Another thing to try is to just download an earlier version of the driver for your card.

I wish I had more experience with this (maybe someone who does will post soon) but this is what worked for me, hopefully it helps you as well.

---

