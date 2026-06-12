---
title: "movie converters help quick please!"
date: 2008-04-11
forum: Multimedia &amp; Video
---

### Post by patrickm918 on 2008-04-11
i need a movie converter for my sandisk sanser and i need one fast that works with ubuntu. The file I have is a DvDrip and i need to convert to like an avi file please help fast as i am leaving for vacation in a few hours.

Thank you and no guides please!!
Just the actual site to the download of this item.

---

### Post by xc3RnbFO8P on 2008-04-11
[Avidemux]("http://www.getdeb.net/app/Avidemux")

---

### Post by bingoUV on 2008-04-11
I'll do quicker. No site to download. 
```

sudo apt-get install mencoder
mencoder -oac lavc -ovc lavc -lavcopts abitrate=112:vbitrate=1500 <input-file> -o <output-file>.avi

```

You will have to play with the abitrate and vbitrate to get acceptable quality vs. file size.

---

### Post by patrickm918 on 2008-04-11
ok it basically restarted my computer when it finished in the terminal now what???

---

### Post by patrickm918 on 2008-04-11
hey how do i actually do the converting please explain

---

### Post by xc3RnbFO8P on 2008-04-11
In avidemux?

---

### Post by ubuntu-freak on 2008-04-11
[www.winff.org](www.winff.org)
 
Make sure you have w32codecs, faac and faad for good measure. Download the older WinFF if you're running Gutsy/Hardy (latest one is being rewritten) and convert the file to a MS compatible avi.
 
Nathan

---

### Post by bingoUV on 2008-04-11
mencoder restarted your computer?

---

### Post by gambrjl on 2008-04-11
I've been working with mencoder for a month to get the right settings for my Creative Zen (I'm a slow learner). 

 but in a pinch pocketdivxencoder will work with wine like a charm

---

