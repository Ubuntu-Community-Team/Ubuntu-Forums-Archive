---
title: "Sansa E250 (R) files -- can add but not delete"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by t2000kw on 2007-11-24
I have a Sansa E250R MP3 player. I have Rock box set up successfully on it. 

I have added some files, and I thought I had deleted files previously, but tonight when I copied some folders to the expansion card and then tried to delete the original folders I got a message that I didn't have the privileges to delete them, that it was read only. 

So why can I write and read to/from the main disk but not delete files? Seems strange to me, but there must be something I need to fix. 

Don

---

### Post by t2000kw on 2007-11-24
IN addition, I cannot "delete the trash" so I have extra stuff on my built in disk and probably the expansion card. Even after removing the expansion card, I have doubles of everything now, probably because I can't delete the trash. 

Please help.

---

### Post by Syspeg on 2008-04-16
I hade the same problem. And i couldn't delet thrash. I even tryed to fix it on a win-pc. 

This is hove i solved it. :)
:( If you do this solution everything saved on the sansa goes away. :( 

1 Install QTParted. 
2 Connect Sansa. 
3 Unmount. 
4 Launch QTParted. 
5 Mark /dev/sda1 rightklick and select format.
6 Chose Fat32 and put in a label. 
7 Last chans to abort. :confused:
8 Click on commit. 
9 All saved files should be gone. :popcorn:

:lolflag: [A swedish guide with picture is availebel here.]("http://syspeg.googlepages.com/sansae250whatyouseeiswhatyouget") :guitar: 

Syspeg

---

