---
title: "Extracting VIDEO_TS"
date: 2008-07-09
forum: Multimedia Software
---

### Post by Thomas Tolleson on 2008-07-09
Hi! I have a wedding DVD with three different movies on it. I've copied the VIDEO_TS and AUDIO_TS folders to my hard drive. The VIDEO_TS folder contains a bunch of different movies, and I'm not sure how to piece this together.

Is there software that I can use to re-piece these VOB files into the three movies that appeared on the DVD?

Thanks!

Thomas Tolleson

---

### Post by mgmiller on 2008-07-09
You can put .vob files into dvdstyler and create a DVD that will play in a set top dvd player.  It even makes simple menus and such.
```

sudo apt-get install dvdstyler
```

---

### Post by Thomas Tolleson on 2008-07-10
I tried to install DVDStyler, but my system couldn't find the package.

Also, I don't want to make a DVD, I want to output the three different movies that are on the DVD from which I copied the VIDEO_TS folder.

That is, the DVD originally had three movies on it. I extracted the VOB files, and now I want to piece them together to create the three movies again in three different mpg files.

Thanks!

Thomas Tolleson

---

### Post by mgmiller on 2008-07-10
> **Thomas Tolleson said:**
> I tried to install DVDStyler, but my system couldn't find the package.

I thought it was in the repositories, but you can get it here:
[http://www.dvdstyler.de/downloads.html](http://www.dvdstyler.de/downloads.html)


> Also, I don't want to make a DVD, I want to output the three different movies that are on the DVD from which I copied the VIDEO_TS folder.

That is, the DVD originally had three movies on it. I extracted the VOB files, and now I want to piece them together to create the three movies again in three different mpg files.I am a little fuzzy on what exactly you are trying to do.  Do you want to create 3 separate mpg files, each of which is a stand alone movie?  What are you trying to "piece together"?

avidemux will open .vob files and let you save them as mpg (as well as several other types of files)  There will be no menus, you won't be joining any files together, and they won't play on a set top dvd player (unless it supports plain mpg files).

```
sudo apt-get install avidemux
```

---

### Post by Thomas Tolleson on 2008-07-10
Yep, I'm trying to create standalone mpg movies. avidemux is working great.

Thanks for all the advice!

Thomas

---

### Post by mgmiller on 2008-07-10
Glad I could help.  Welcome to the Ubuntu community.

If you would like to "officially" thank me, just click on the little gold star in the lower right corner of my post that you found helpful.

:popcorn:

---

