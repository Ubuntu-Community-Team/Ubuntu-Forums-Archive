---
title: "Editing DVD"
date: 2008-05-23
forum: Multimedia Software
---

### Post by brunog on 2008-05-23
I have a DVD recorder which I use to record programs on TV. This recored is of the older sort - write directly to disc, not HD installed.
Each DVD contains different programs - some for the kids some for myself.
I would like to import the DVD into software, and then separate my programs from the kid's and write them to a new disk.
I have downloaded a few editing tools DeeVeeDee, Cinelerra etc, but they all seem to want avi files or the like.  None seem to have the function of importing a whole DVD from the DVD drive and allowing me to edit it.

Any ideas on how I can import a DVD and then selectively copy sections and write these to another DVD?

Thanks for assisting.

---

### Post by xc3RnbFO8P on 2008-05-23
Use Devede, you can multi add film files.
Choose DVD> convert files to mpeg
You can drag and drop files from file manager into Devede.

---

### Post by esaym on 2008-05-28
Yea I have this exact same problem.  I would like edit the dvd though to take out the commercials.  Having trouble figuring that out.

edit:
alright, looks like avidemux might be able to do this.  I will have to mess with it once I get off of work tonight.

[http://ubuntuforums.org/showthread.php?t=672066](http://ubuntuforums.org/showthread.php?t=672066)

---

### Post by jethro10 on 2008-05-29
Most (all?) tools I've come across wont work with a DVD itself as they have VOB video files on them which are Basically mpeg 2 files but split to suit the DVD like chapter marks and menu structures etc.

things like Dvd::rip extract these, possibly multiple files and make a single .avi for each title/menu option on the DVD.

You almost certainly are going to have to strip off using a package like this (maybe one does mpeg 2 files so wont re-code, I dont know) then re make DVD's from these with DeVeDe or similar. If it make a re-code you will loose quality and lots of time :-(

My preference would be passing raw VOB's renamed as .mpg (I think it works - check that avidemux may accept raw VOB's, it might) thru avidemux to edit out the adverts etc then use DVDStyler to create new DVD's

I am almost sure you can copy vobs directly off your home made DVD with nautilus, rename them from .vob to .mpg then join them in avidemux, edit your bits out, re-save WITHOUT recoding so it will be MUCH quicker, then use DVDStyler to make new dvd's from these mpeg's

avidemux is in the repo's and a newish dvdstyler can be got from here [http://www.getdeb.net/search.php?keywords=dvdstyler](http://www.getdeb.net/search.php?keywords=dvdstyler)

Jeff

---

### Post by esaym on 2008-05-30
ah avidemux works great for this!

[http://www.avidemux.org/admWiki/index.php?title=DVD_to_AVI](http://www.avidemux.org/admWiki/index.php?title=DVD_to_AVI)

Not bad at all.  It was kind of tricky figuring out how to encode the video right but just read the heck out of the wiki.

And yes you can edit any commercials out:
[http://www.avidemux.org/admWiki/index.php?title=Cutting](http://www.avidemux.org/admWiki/index.php?title=Cutting)

---

### Post by jethro10 on 2008-05-30
> **esaym said:**
> ah avidemux works great for this!

 It was kind of tricky figuring out how to encode the video right but just read the heck out of the wiki.



This is avidemux biggest issue, its briliant at what it does, but is difficult to get into.

J

---

### Post by esaym on 2008-05-30
It appears that the next catch is that the video coming out of my tv cable box is interlaced which really degrades the quality.  I guess this is the disadvantage of doing it this way instead of buying a video recorder card for my computer?

---

