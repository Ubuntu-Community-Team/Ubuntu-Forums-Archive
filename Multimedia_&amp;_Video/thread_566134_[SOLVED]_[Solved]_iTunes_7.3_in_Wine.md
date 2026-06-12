---
title: "[SOLVED] [Solved:] iTunes 7.3 in Wine"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by justinmiller87 on 2007-10-03
I was looking around the Internet and came across the following blog that got one of the latest versions of iTunes installed, so I figured I would share the link.

I don't take credit for figuring it out, only for finding it. I also should point out that I haven't tried it yet, but the information is there for you to try it out.

[http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html)

---

### Post by carpex on 2007-10-03
This doesn't work for me in a existing wine install :( It tells me that it needs XP or Vista, even thought I tell winecfg to mimic WinXP. ;-(

CP

---

### Post by justinmiller87 on 2007-10-03
> **carpex said:**
> This doesn't work for me in a existing wine install :( It tells me that it needs XP or Vista, even thought I tell winecfg to mimic WinXP. ;-(

CP
If you check out the comments on the blog, you're not alone. There's some other people who ran into the same issues and the author of the page has since given updates, such as to where to get the [RichEdit dll](http://www.hexagora.com/download/support/riched30.exe) files in question and what version of WINE you have to use (0.9.45 or newer).

---

### Post by ubuntios on 2007-11-18
> **justinmiller87 said:**
> I was looking around the Internet and came across the following blog that got one of the latest versions of iTunes installed, so I figured I would share the link.

I don't take credit for figuring it out, only for finding it. I also should point out that I haven't tried it yet, but the information is there for you to try it out.

[http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html)

Hi ,
I'd like to confirm that iTunes 7.5 working with wine, The only problem on iTunes for all the versions is that it doesn't  recognize the ipod's.

---

### Post by hansteam on 2007-11-18
When I type $wine iTunesSetup.exe I get this error:

```
wine: could not load L"c:\\windows\\system32\\iTunesSetup.exe": Module not found

```

---

### Post by kansukee on 2007-11-18
You can get the dll update from here: [http://media.codeweavers.com/pub/crossover/office/support/richedit30.exe](http://media.codeweavers.com/pub/crossover/office/support/richedit30.exe)

I did it and it worked for me.

---

