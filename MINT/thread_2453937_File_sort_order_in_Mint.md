---
title: "File sort order in Mint"
date: 2020-11-19
forum: MINT
---

### Post by fooger on 2020-11-19
I installed Mint a few days ago and I've been trying to get help about how files are sorted in file managers. I have posted my issue in Linux Mint Forum but there doesn't seem to be any resolution for my problem so I thought I'd try to get some help here.
I don't want to spend the time trying out different distro's but I need this to work as I have thousands of named folders in sub directories in folders named A,B,C etc. and don't want to accidentally miss someone while looking for their name. What I need is the left hand column what I get in Nemo is the right hand column:


Alex A____________________Alex A
Alex B____________________Alexander F
Alex H____________________Alexander K
Alex R____________________Alexander R
Alexander F_______________Alex B
Alexander K_______________Alex H
Alexander R_______________Alexis C
Alexis C__________________Alexis E
Alexis E__________________Alexis P
Alexis P__________________Alex R

This also happens with Thunar and Command Line, screenshots below:

[ATTACH=CONFIG]287387[/ATTACH]

[ATTACH=CONFIG]287388[/ATTACH]



I know the problem is not specific to Nemo as shown above but even if I knew whether it was a Mint, Debian or Linux issue I could make a decision on where to go from here.
If someone with Gnome, Mate, Xfce or any other version could take a couple of minutes to try this so I might be able to narrow the problem down it would be very much appreciated.


Thanks for any help, or advise.

---

### Post by howefield on 2020-11-19
Thread moved to the "*MINT*" forum.

---

### Post by CelticWarrior on 2020-11-19
Welcome.

Not a problem, not an issue, therefore there's no "solution".
When sorting alphabetically it does exactly that and by "it" I mean all of them, in any distro or any OS family, including Windows or Apple.
When sorting alphabetically spaces are ignored (and so is capitalization). As such "Alex A" = "alexa" and "Alex B" = "alexb". Logically, "alexander..." comes after "alexa" and before "alexb".

---

### Post by fooger on 2020-11-19
Thanks for the reply CelticWarrior.

I have been accessing these files in Windows 7 for several years and Window 10 for the last while and they have always been sorted as the first column. My wife is away with her Ipad but I got her to try it and it is sorted the same as Windows. 
Here are some screenshot from windows and my android phone:

[ATTACH=CONFIG]287389[/ATTACH]
[ATTACH=CONFIG]287390[/ATTACH]

So I'm guessing if what you are saying is correct there is no chance of having this sort as per column 1 in anything Linux.

---

### Post by fooger on 2020-11-19
Okay I did some testing myself, I burned Ubuntu and MX Linux both of which have different file managers then Mint and ran them from a disk. Same problem with the sort order on all of them so this leads me to believe it's a Linux issue. In Windows 7 and 10, Mac's(at least an Ipad) and Android all files a sorted like the left column, I also checked some online dictionaries and they also seem to sort like the left had column. For me where there are hundreds of names in some folders some first names are spread across dozens of different names.

Alex A____________________Alex A
Alex B____________________Alexander F
Alex H____________________Alexander K
Alex R____________________Alexander R
Alexander F_______________Alex B
Alexander K_______________Alex H
Alexander R_______________Alexis C
Alexis C___________________Alexis E
Alexis E___________________Alexis P
Alexis P___________________Alex R

If anyone knows of a way this can be changed maybe similar to the way you can change the time and date formats I would really appreciate the help it would make life much easier for me.

---

### Post by fooger on 2020-11-20
I have found a Very Simple solution to my problem. I installed Dolphin everything is sorted correctly now.

---

