---
title: "How to play music zip/rar/7z files in Ubuntu"
date: 2012-04-14
forum: Multimedia Software
---

### Post by shantiq on 2012-04-14
So i recently discovered this and thought to share as probably few know this   



if you have a collections of music tracks zipped or in a rar or 7z compressed folder   these will play AND separate in VLC


and command line with nvlc and cvlc


so for example go to where you zip is and write


```
nvlc mymusicfile.zip
```   



**can also be done**   with Foobar under Wine but need to remember to click archive manager during install and to add [**this component** ]("http://www.foobar2000.org/components/view/foo_unpack_7z")to enable 7z

[CENTER][ATTACH]215994[/ATTACH][/CENTER]



**do we know any other players you know that can do this?**

---

### Post by TenPlus1 on 2012-04-14
Why do you have your music collection archived ?

---

### Post by shantiq on 2012-04-14
like it that way.  Tidy.  Only one file per album.

---

### Post by andrew.46 on 2012-04-16
> **shantiq said:**
> do we know any other players you know that can do this?]

MPlayer can do this in a slightly more round-about way:


```
unzip -p test.zip | mplayer -cache 2048 -
```

Similar examples in Tip2 here:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

See it here before it is wikified :).

---

### Post by shantiq on 2012-04-16
excellent Andrew and thank you


sadly so far not very successful on my system with zip :KS

---

