---
title: "Locate wireless drivers on windows XP"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by swimon on 2010-10-10
Hi, 

I'm going to install ubuntu on my computer, currently it has windows XP installed.

I'm trying to locate the wireless drivers because I will use them for NDIS wrapper when I have ubuntu installed.

But i'm not sure where I can find them and what the names of the files are.

Thanks

---

### Post by swimon on 2010-10-11
is this a stupid question?

---

### Post by chili555 on 2010-10-11
> **swimon said:**
> is this a stupid question?Not at all. However, without knowing the type of wireless card you have, we'd have no way to know the name of these files, except we know they are .inf and, possibly .sys files.

Please run these terminal commands to help you find the card you have:```
lspci -nn
lsusb
```Then search this forum and here: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?mediawiki/index.php/List](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?mediawiki/index.php/List)

Many of us here, maybe most of us, do not have any Windows installations. I assume you can search for files and folders for the files you need.

---

### Post by swimon on 2010-10-12
Oh, but I haven't installed yet on my machine. 

When I tried ubuntu for the first time a couple of years ago, I remember some people recommending to copy the wireless drivers in windows, and then to use them with NDIS-wrapper. 

Is this still a valid solution?

---

### Post by pricetech on 2010-10-12
Maybe.  Some wireless cards will just work.  Others need a little help.  Sadly, wireless vendors don't seem to consider Linux worth their while.

In answer to your original question;  In device manager, choose your wireless card, right click and select Properties.  Click the Driver tab and you'll be able to find the details showing what files are used.

I'm pretty sure that ndiswrapper lets you use a windows driver though, so you probably want to download the latest from the card manufacturer's website.  If I'm wrong about that, hopefully someone will correct me.

Having said all that;  Try it first before you start adding drivers of any kind and read up here in the forums.  Stick with the simplest solution that works.

Good luck with it and enjoy Ubuntu.

---

### Post by swimon on 2010-10-14
thanks for the replies. I think I know how to figure it out now.

the only problem is a non-linux related one... I can't seem to remember where I left my old notebook :D

---

### Post by smilodonis on 2010-10-14
Probably, your wifi card will work out of the box on 10.10.

---

### Post by swimon on 2010-10-17
> **smilodonis said:**
> Probably, your wifi card will work out of the box on 10.10.

You're right it did

> **swimon said:**
> is this a stupid question?

Turns out it was a stupid question after all :)

But thanks everyone for helping!

Grtz

---

