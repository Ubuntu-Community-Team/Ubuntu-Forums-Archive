---
title: "extracting files for ndiswrap failing"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by octobear on 2010-02-08
The problem, chaps, is that my ar928x atheros wireless connection is severely slow. To fix it I've heard ndiswrap and so I've downloaded the XP driver from HP's support site (a pavilion dv7-1450us Notebook PC) and met a brick wall. The file is sp45222.exe and it contains seemingly no .bin .inf or .sys files that ndiswrap dearly requires. I've tried extracting it on a windows machine with UniExtract. This gives only three files one of which UniExtract can extract into a compilation of folders none of which have the required files. I've also attempted to use cabextract on my Ubuntubox, but not cabs come out. I have unshield, if that's relevant at all. What on Earth am I doing wrong? 

PS: I've only used Linux for a few days so keep it readable if possible. Thanks if you can help.

---

### Post by bkratz on 2010-02-08
Here is a similar thread you might want to read it may offer some help
(esp. post 5)
[http://ubuntuforums.org/showthread.php?p=8599246#post8599246](http://ubuntuforums.org/showthread.php?p=8599246#post8599246)

---

### Post by octobear on 2010-02-09
The question is more file-specific for me. Where are those .bin .sys and .inf files?

---

### Post by bkratz on 2010-02-09
> **octobear said:**
> The question is more file-specific for me. Where are those .bin .sys and .inf files?




I believe that I found the .inf file online for XP, this is for 32 bit, but the 64 bit was also on this site. Not speaking this language, it looks like it might be what you want?


[http://www.atheros.cz/inffile.php?inf=66&bit=32&atheros=AR928X&system=1](http://www.atheros.cz/inffile.php?inf=66&bit=32&atheros=AR928X&system=1)



Here is the main page
[http://www.atheros.cz/download.php?atheros=AR928X&system=1](http://www.atheros.cz/download.php?atheros=AR928X&system=1)

---

