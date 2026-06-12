---
title: "Where is Lubuntu 10.10?"
date: 2010-10-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by shuttleworthwannabe on 2010-10-09
Any idea if the daily builds cdimage will be released? we are closing in to the final release, the site is still stuck in beta?

A link to the daily release will help.
Tx,
S

---

### Post by 23meg on 2010-10-09
Lubuntu is not among the official builds this cycle.

[https://lists.launchpad.net/lubuntu-desktop/msg02311.html](https://lists.launchpad.net/lubuntu-desktop/msg02311.html)

---

### Post by shuttleworthwannabe on 2010-10-09
thanks--I was aware of that fact, but wanted to know how to keep up with the development (albeit not official). IMHO, this project has a huge future for our aging machines (5yrs+). It also is a handy tool to recover discs through live instalation.

Anyway, I will wait for the official call from their website. At least now we have the 10.10 beta 2 release.

Great work.
S

---

### Post by jerrylamos on 2010-10-09
> **mgunes said:**
> Lubuntu is not among the official builds this cycle.

[https://lists.launchpad.net/lubuntu-desktop/msg02311.html](https://lists.launchpad.net/lubuntu-desktop/msg02311.html)
Lubuntu is my preferred Ubuntu on two of my four test pc's, this one a 1 gHz Thinkpad and also on a 2 gHz Think Centre with integrated intel i845G video graphics.

Lubuntu is noticeably crisper and more responsive than straight Ubuntu Maverick on those pc's.  My other two pc's a 1.5 Ghz Pentium Thinkpad and a 3.33 gHz Celeron tower are fast enough with regular Gnome & Firefox.  Lubuntu is eyeblink fast on them also.

Having said that, I'm still struggling with Lubuntu's internet browser Chromium with simple things like Bookmark managing.  Firefox is pretty sluggish (!) on the slower machines.

Pcmanfm file manager is also a difficulty since then I select an icon which is a shell script it does not execute (?).  Pcman on Debian does.  Nautilus is sluggish but it does have function.

I have run Xubuntu in the past.  Lubuntu in my opinion is a better choice.

Jerry

---

### Post by ronacc on 2010-10-09
jerry give Opera a try , works fine in Lubuntu for me .

---

### Post by ronacc on 2010-10-09
hmm just for grins I tried launching gnome-shell from Lubuntu , interesting :P

---

### Post by shuttleworthwannabe on 2010-10-09
Guys, Are you all using the beta 2 release?

---

### Post by 23dornot23d on 2010-10-09
> **ronacc said:**
> hmm just for grins I tried launching gnome-shell from Lubuntu , interesting :P

I like this , also added cairo-dock to it too ..... GL mode ..... works well 

[SCREENSHOT]("http://img259.imageshack.us/img259/4397/screenshot6b.png")

What is interesting is the memory usage ..... 

[Memory used]("http://img827.imageshack.us/img827/9458/screenshot9s.png") 

I am using the latest version of Lubuntu from the repositories .... not sure how you show the version ?

[System Info]("http://img37.imageshack.us/img37/7166/screenshot10t.png")

---

### Post by ubunterooster on 2010-10-09
> **shuttleworthwannabe said:**
> Any idea if the daily builds cdimage will be released? we are closing in to the final release, the site is still stuck in beta?

A link to the daily release will help.
Tx,
S
Do a minimal install of the RC Ubuntu, then run ```
sudo apt-get install lubuntu-desktop
```

---

### Post by jerrylamos on 2010-10-09
> **ubunterooster said:**
> Do a minimal install of the RC Ubuntu, then run ```
sudo apt-get install lubuntu-desktop
```

Lubuntu Beta's on a couple of my older test pc's.  Lxde is quick and usable.  I've been fighting Chromium for some time - finally tried Firefox4 which seems to be as fast or faster on videos...

I made a shell script called firefox4 as follows:
```

#! /bin/bash
echo "http://twitteling.com/2010/07/how-to-install-the-firefox-browser-beta-4-on-ubuntu/"
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
sudo apt-get update
sudo apt-get install firefox-4.0
exit #

```

It says it takes 30 mb of disk space, I think more like 40 mb.

Jerry

---

