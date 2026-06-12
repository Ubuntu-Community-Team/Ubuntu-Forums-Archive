---
title: "3D acceleration on Dynabook CX laptop (Intel driver)"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by andyket on 2006-07-26
I recently installed Ubuntu 6.06 on my Toshiba Dynabook CX/3216LMSWBB laptop - everything works great, but I have a question about installing video drivers (as Google Earth needs 3D acceleration).

Info about my system via lspci:
[INDENT]0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)[/INDENT]

I suppose I have to install [these drivers]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=922&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21").

But which one of the three? And how to proceed? (there are e.g. Suse specific instructions, but those are probably not very helpful)

Any help (esp. step-by-step commandline instructions) is appreciated.

---

### Post by rpw on 2006-08-01
Hello andyket,

when I look into the readme.txt of the first download on this website, I can see that the 855GM is mentioned. I would sugguest this driver, because the other ones are bloody old (from 2004).

rpw

---

### Post by shadyzay on 2007-03-21
did you get any luck with this, I got the same graphics card on my Gateway 4542GP, and running googleearth is not fun at all!

---

